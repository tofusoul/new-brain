# KDE

- Compositor

- \[Alt]+[Shift]+\[F12] restarts compositor

## Tips and Tricks

### Desktop Customization
*   **Classic "Start" Menu**: Right-click the Application Launcher (start menu icon) → Alternatives → Application Menu.
*   **Pin Apps to Taskbar**: Launch an app, then right-click its icon in the Taskbar → Check "Show Launcher When Not Running".
*   **Disable Top Left "Hot Corner"**: Go to System Settings → Desktop Behaviour → Screen Edges. Set the Top Left edge to "No Action".
*   **Don’t sort windows in Taskbar**: Right Click the empty area on the taskbar → Task Manager Settings → General Tab → Sorting: Manual. Uncheck "Keep Launchers Separate".

### Keyboard Shortcuts & Window Management
*   **Open "Start Menu" with Windows/Meta key**: This is often the default. If not, right-click the Application Launcher icon → Configure Application Launcher → Keyboard Shortcuts tab. Ensure a shortcut like `Alt+F1` is set. The Meta key should then trigger it.
*   **Useful Window Keybindings (set in System Settings → Shortcuts → Global Keyboard Shortcuts → KWin):**
    *   Show Desktop: `Win+M` (or `Win+D`)
    *   Maximize Window: `Win+Up`
    *   Minimize Window: `Win+Down`
    *   Quick Tile Window to the Left: `Win+Left`
    *   Quick Tile Window to the Right: `Win+Right`
*   **Change Alt+Tab popup style**: System Settings → Window Management → Task Switcher. You can select different styles like "Thumbnail Grid".
*   **Hide titlebars when maximized**:
    ```bash
    kwriteconfig5 --file ~/.config/kwinrc --group Windows --key BorderlessMaximizedWindows true
    qdbus org.kde.KWin /KWin reconfigure
    ```
