# Add "Open in VSCode" to Windows Context Menu

## Basic Process

> :warning: **Making changes to the Windows registry can cause major problems, ensure that you understand what you are doing and take a backup prior to making these changes.**

1) Create a new "Key" in the Windows registry at `HKEY_CLASSES_ROOT\Directory\shell\`
    - For Only the current User use `HKEY_CURRENT_USER\Software\Classes\directory\shell`
2) Within that key create a string value called icon that points to the icon you wish to use.
3) Edit the "(Default)" value for that fold to be the name of the context menu item.
4) Create another key within the key made in step 1
5) Set the "(Default)" value to the path to VSCode, append `"%V"` at the end to pass the clicked on folder as a parameter to VSCode `"C:\Program Files\Microsoft VS Code\code.exe" "%V"`
6) Repeat this process in `HKEY_CLASSES_ROOT\Directory\Background\shell\` to add it to the context menu when you click in the 'background' of a folder.
    - For Only the current user use `HKEY_CURRENT_USER\Software\Classes\directory\Background\shell`

## Prebuilt Registry Files

> :warning: **Importing .reg files without understanding their contents is incredibly dangerous.**

[With Administrator Privileges / For All Users](vscodecontextmenu_allusers.reg)

[Without Administrator Privileges / For only Current User](vscodecontextmenu_currentuser.reg)