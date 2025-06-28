# Useful Keyboard Shortcuts for Windows, Google Chrome, VS Code

## Windows Window Management Shortcuts

| Action                                 | Shortcut            | Description                                    |
|----------------------------------------|---------------------|------------------------------------------------|
| Snap window to the left half           | `Win` + `←`         | Move active window to the left half of screen  |
| Snap window to the right half          | `Win` + `→`         | Move active window to the right half of screen |
| Maximize window                        | `Win` + `↑`         | Maximize the current window                    |
| Restore/minimize window (from max)     | `Win` + `↓`         | Restore down or minimize the window            |
| Snap window to top-left corner         | `Win` + `←` then `↑`| Move window to top-left quarter of screen      |
| Snap window to bottom-left corner      | `Win` + `←` then `↓`| Move window to bottom-left quarter of screen   |
| Snap window to top-right corner        | `Win` + `→` then `↑`| Move window to top-right quarter of screen     |
| Snap window to bottom-right corner     | `Win` + `→` then `↓`| Move window to bottom-right quarter of screen  |
| Cycle through open windows             | `Alt` + `Tab`       | Switch between open windows/apps               |

---

## Google Chrome Common Shortcuts

| Action                                 | Shortcut (Windows)        | Description                                    |
|----------------------------------------|---------------------------|------------------------------------------------|
| Open Downloads                         | `Ctrl` + `J`              | Open downloads page                            |
| Open History                           | `Ctrl` + `H`              | Open browsing history                          |
| Open New Tab                           | `Ctrl` + `T`              | Open a new tab                                 |
| Close Current Tab                      | `Ctrl` + `W`              | Close active tab                               |
| Switch to Next Tab                     | `Ctrl` + `Tab`            | Cycle forward through open tabs                |
| Switch to Previous Tab                 | `Ctrl` + `Shift` + `Tab`  | Cycle backward through open tabs               |
| Open New Window                        | `Ctrl` + `N`              | Open a new browser window                      |
| Open New Incognito Window              | `Ctrl` + `Shift` + `N`    | Open a new incognito window                    |
| Reload Page                            | `Ctrl` + `R`              | Reload current page                            |
| Reload Page (ignore cache)             | `Ctrl` + `Shift` + `R`    | Reload page ignoring cache                     |
| Zoom In                                | `Ctrl` + `+`              | Zoom in                                        |
| Zoom Out                               | `Ctrl` + `-`              | Zoom out                                       |
| Reset Zoom                             | `Ctrl` + `0`              | Reset zoom level                               |
| Open Developer Tools                   | `Ctrl` + `Shift` + `I`    | Open Chrome DevTools                           |
| Open JavaScript Console                | `Ctrl` + `Shift` + `J`    | Open JS console inside DevTools                |
| Inspect Element                        | `Ctrl` + `Shift` + `C`    | Toggle element inspector mode                  |
| Focus Address Bar (Omnibox)            | `Ctrl` + `L`              | Focus the URL bar                              |

---

## VS Code Window and Editor Management Shortcuts

| Action                                 | Shortcut (Windows)        | Description                                    |
|----------------------------------------|---------------------------|------------------------------------------------|
| Open/close integrated terminal         | `Ctrl` + `J`              | Show or hide the terminal panel                |
| Toggle sidebar visibility              | `Ctrl` + `B`              | Show or hide the sidebar                       |
| Split editor (vertical)                | `Ctrl` + `\`              | Split the current editor into two side-by-side |
| Close current editor                   | `Ctrl` + `W`              | Close the active editor                        |
| Find in current file                   | `Ctrl` + `F`              | Search text in the current file                |
| Replace in current file                | `Ctrl` + `H`              | Find and replace text in the current file      |
| Search across all files                | `Ctrl` + `Shift` + `F`    | Search in the entire project                   |

* You can enable regex search by clicking the `.*` icon in the search panel.

### 🔎 Regex in VS Code

#### Example: Convert all Markdown bullet points from `*` to `-`

> * **Find**: `^\*`
> * **Replace**: `-`

This avoids matching other `*` characters, like the ones used for **bold**. Regular expressions are more precise than just using the `Aa` (case-sensitive) or `ab` (whole word) options.
