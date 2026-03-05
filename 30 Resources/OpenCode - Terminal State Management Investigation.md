---
Type: Resource
tags: [resource, opencode, terminal, debugging, troubleshooting]
---

# OpenCode - Terminal State Management Investigation

**Investigation Date:** 2025-10-05
**Focus:** Terminal state management and TUI cleanup in OpenCode

## Summary
Investigation into how OpenCode detects and manages terminal environments, specifically addressing terminal state issues when the TUI exits.

## Architecture Overview

### Client/Server Model
- **CLI:** TypeScript-based (entry point)
- **TUI:** Go-based using Charm's Bubble Tea v2 framework

### Key Files Examined
- `packages/opencode/src/cli/cmd/tui.ts` - TypeScript TUI command handler
- `packages/opencode/src/index.ts` - Main CLI entry point
- `packages/tui/cmd/opencode/main.go` - Go TUI entry point
- `packages/tui/internal/components/chat/message.go` - ANSI escape handling
- Local: `/home/tofu/.local/share/nvim/lazy/opencode.nvim/`

## Technical Findings

### Bubble Tea Framework Configuration
OpenCode uses Bubble Tea v2 with these options:
```go
program := tea.NewProgram(
    tuiModel,
    tea.WithAltScreen(),
    tea.WithMouseCellMotion(),
)
```

### ANSI Escape Sequences
- **Fix found in PR #1139:** Strips ANSI sequences using `ansi.Strip()` for bash command output
- Handles terminal escape codes properly

### Terminal Detection
- **No explicit terminal detection** found in main.go
- Uses standard stdin/stdout handling
- Relies on Bubble Tea's built-in terminal management

### Environment Variables
- `OPENCODE_SERVER` - Server endpoint
- `CGO_ENABLED=0` - Go compilation flag
- `OPENCODE=1` - OpenCode flag

## Root Cause Analysis

### The Problem
When OpenCode exits:
- Terminal may be left in alt-screen mode
- Cursor settings may not be restored
- Shell prompt may not display properly

### Signal Handling Code
```go
sigChan := make(chan os.Signal, 1)
signal.Notify(sigChan, syscall.SIGTERM, syscall.SIGINT)

go func() {
    sig := <-sigChan
    slog.Info("Received signal, shutting down gracefully", "signal", sig)
    tuiModel.Cleanup()
    program.Quit()  // ISSUE: May not trigger proper cleanup
}()
```

### The Issue
**`program.Quit()` likely calls Bubble Tea's `kill()` method, not `stop()`**:
- No final frame rendering
- **Potentially no `exitAltScreen()` call**
- Terminal left in alt-screen mode

## Bubble Tea Terminal State Management

### Proper Bubble Tea Behavior
- `start()`: Initializes renderer and starts render loop
- `stop()`: Renders final frame and cleans up properly
- `kill()`: **Immediate termination without final render**

### AltScreen Management
- `enterAltScreen()`: Uses `ansi.SetAltScreenSaveCursorMode`
- `exitAltScreen()`: Uses `ansi.ResetAltScreenSaveCursorMode` (properly restores terminal state)

## Potential Solutions

### 1. Fix Signal Handling
Replace `program.Quit()` with proper quit message:
```go
go func() {
    sig := <-sigChan
    slog.Info("Received signal, shutting down gracefully", "signal", sig)
    program.Send(tea.QuitMsg{})  // Send quit message instead
}()
```

### 2. Ensure Proper Cleanup
The `tuiModel.Cleanup()` method should ensure:
- Bubble Tea's renderer is properly stopped
- Alt-screen mode is exited
- Terminal state is restored

### 3. Workarounds for Users
Manually restore terminal after crash:
```bash
# Reset terminal state
reset
# Or
stty sane
tput reset
```

## Next Steps

### Investigation Needed
1. [ ] Find actual TUI model implementation (local installation)
2. [ ] Locate `Cleanup()` method implementation
3. [ ] Test current behavior to confirm root cause
4. [ ] Develop patch for proper terminal state management

### Terminal State Validation
Test for alt-screen mode:
```bash
echo -e "\e[?1049$p"  # Should return 0 if not in alt-screen
```

## Related Notes
- [[Customizing Opencode for Personal Workflow]] - Main customization project
- [[Terminal]] - Terminal emulator resources
- [[Bubble Tea]] - TUI framework documentation
- [[OpenCode]] - General OpenCode resources

## Key Insights
- **The issue is in OpenCode's integration with Bubble Tea, not Bubble Tea itself**
- **Bubble Tea has proper terminal state management; OpenCode may not be using it correctly**
- **Signal handling needs to use `program.Send(tea.QuitMsg{})` instead of `program.Quit()`**

---
*Last updated: 2025-02-01*
