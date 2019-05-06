activate application "SystemUIServer"
tell application "System Events"
    tell process "SystemUIServer"
        set btMenu to (menu bar item 1 of menu bar 1 whose description contains "bluetooth")
        tell btMenu
            click
            tell (menu item "NAME_OF_YOUR_AIRPODS" of menu 1)
                click
                if exists menu item "Connetti" of menu 1 then
                    click menu item "Connetti" of menu 1
                    return "Connecting..."
                else
                    key code 53
                    return "Connect menu was not found, are you already connected?"
                end if
            end tell
        end tell
    end tell
end tell
