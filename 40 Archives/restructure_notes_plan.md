# Comprehensive Plan for Restructuring Notes with Link Preservation

## Executive Summary

This plan outlines a reliable approach to restructure the Obsidian vault according to
the PARA method while preserving all internal wiki links. The plan includes multiple
approaches to ensure success and prevent recurrence of the issues experienced with
Gemini's migration attempt.

## Approach 1: Using Obsidian Local REST API (Primary Method)

### Prerequisites
1. Obsidian must be running with the Local REST API plugin enabled
2. API Key: `9bb48ab76b7b9145cb813dca8b11118faedb488e2b9ff1c0c5de4da4dbe26238`
3. API Port: `27123` (insecure) or `27124` (secure)

### Process
1. **Pre-flight Check**: Verify API is accessible:
   ```bash
   curl -H "Authorization: Bearer 9bb48ab76b7b9145cb813dca8b11118faedb488e2b9ff1c0c5de4da4dbe26238" \
        http://localhost:27123/
   ```

2. **File Movement with Link Updates**:
   - Use the API's file move/rename endpoint (exact endpoint to be determined through
     testing)
   - The API should automatically update wiki links when files are moved

3. **Batch Processing**:
   - Process files in small batches to ensure reliability
   - Validate each move operation before proceeding

### Fallback if API Endpoints Unclear
If the exact API endpoints for moving files aren't working:
1. Use the API to read file content
2. Create new files in the correct locations
3. Use the API to delete old files
4. Manually update backlinks using regex/text replacement

## Approach 2: Custom Python Script (Secondary Method)

### Key Features
1. **Link-Aware File Movement**:
   - Identify all backlinks to a file before moving
   - Automatically update wiki links in all referencing files
   - Preserve all file content and metadata

2. **Safe Execution**:
   - Dry-run mode to preview changes
   - Git integration to track and rollback changes if needed
   - Comprehensive logging for troubleshooting

3. **Validation**:
   - Pre-move validation of file paths
   - Post-move verification of link integrity
   - Automated testing of critical functionality

### Implementation Steps
1. Parse the vault structure plan from `Final Vault Structure Plan.md`
2. Create a mapping of current file locations to new locations
3. For each file to be moved:
a. Find all backlinks using regex: `grep -r --include='*.md' -l
     '\\[\\[filename_without_extension\\]\\]' .`
   b. Move the file to its new location
   c. Update all backlinks in referencing files
   d. Verify the move was successful
4. Handle special cases:
   - File merging (e.g., `Project Plan App.md` → `Enviroflow App.md`)
   - Files to be deleted
   - Files to be refactored into smaller notes

## Approach 3: Manual Curation Protocol (Backup Method)

This is the manual protocol detailed in the existing plan, preserved as a reliable fallback:

1. **Select & Analyze**: Read the note to understand its content and identify issues
2. **Curate & Enrich**: Clean up formatting, fix errors, and flesh out content
3. **Re-evaluate Placement**: Confirm the note's final destination according to PARA
4. Find Backlinks: Use `grep -r --include='*.md' -l '[[note name]]' .` to find
   referencing files
5. **Move File**: Use `mv "old/path/to/note.md" "new/path/to/note.md"`
6. **Update Backlinks**: Manually edit each referencing file to point to the new location
7. **Verify**: Confirm the move and link updates before proceeding

## Risk Mitigation Strategies

### Prevention of Recurrence
1. **Git Integration**: Commit changes incrementally with descriptive messages
2. **Backup Strategy**: Create a git branch before starting the migration
3. **Validation Checks**: Verify each file move before proceeding to the next
4. **Testing Protocol**: Test on a small subset of files first

### Error Handling
1. **Rollback Capability**: Use git to revert changes if issues are detected
2. **Logging**: Comprehensive logging of all operations for troubleshooting
3. **Checkpoint System**: Save progress at regular intervals to resume from failures

## Implementation Timeline

### Phase 1: Preparation (1-2 hours)
- Set up development environment
- Create backup branch
- Test API connectivity
- Validate file mapping

### Phase 2: Pilot Testing (2-3 hours)
- Test approach on a small subset of files (5-10)
- Validate link preservation
- Refine process based on results

### Phase 3: Full Migration (8-12 hours)
- Execute full migration in batches
- Monitor for issues
- Validate results periodically

### Phase 4: Verification (2-3 hours)
- Comprehensive link checking
- Manual spot-checking
- Final validation

## Success Criteria

1. All files moved to correct PARA locations
2. All internal wiki links functional
3. No data loss or corruption
4. Git history preserved appropriately
5. Vault organization matches the plan in `Final Vault Structure Plan.md`

## Tools and Dependencies

### Required Tools
- Python 3.8+
- Obsidian with Local REST API plugin
- Git for version control
- Standard Unix tools (grep, mv, etc.)

### Python Dependencies
- requests (for API interaction)
- pathlib (for path manipulation)
- re (for regex operations)

## Validation and Testing

### Pre-execution Validation
- Verify all source files exist
- Verify destination directories exist or can be created
- Validate file mapping against the plan

### Runtime Validation
- Confirm each file move succeeds
- Verify link updates in referencing files
- Check for broken links after each batch

### Post-execution Validation
- Comprehensive link integrity check
- Manual verification of critical files
- Git diff review for unexpected changes

## Rollback Plan

If critical issues are detected:
1. Immediately stop the migration process
2. Use git to identify and revert problematic changes
3. Document the issue and adjust the approach
4. Resume migration from the last known good state

## Expected Outcomes

Upon successful completion:
- Vault organized according to PARA method
- All internal links preserved and functional
- Files in correct locations as specified in the plan
- Improved note organization and discoverability
- Enhanced productivity through better information architecture