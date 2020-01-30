set NOME_DI_AIRPODS to "NAME_OF_YOUR AIRPODS"

activate application "SystemUIServer"
tell application "System Events"
	tell process "SystemUIServer"
		
		set btMenu to (menu bar item 1 of menu bar 1 whose description contains "bluetooth")
		tell btMenu
			click
			if exists menu item "Attiva Bluetooth" of menu 1 then
				click menu item "Attiva Bluetooth" of menu 1
				delay 2
				tell btMenu
					click
					tell (menu item NOME_DI_AIRPODS of menu 1)
						click
						if exists menu item "Connetti" of menu 1 then
							click menu item "Connetti" of menu 1
							return "Connecting..."
						else
							key code 53
							-- click btMenu -- Close main BT drop down if Connect wasn't present
							return "Connect menu was not found, are you already connected?"
						end if
					end tell
				end tell
			else
				tell (menu item NOME_DI_AIRPODS of menu 1)
					click
					if exists menu item "Connetti" of menu 1 then
						click menu item "Connetti" of menu 1
						return "Connecting..."
					else
						key code 53
						-- click btMenu -- Close main BT drop down if Connect wasn't present
						return "Connect menu was not found, are you already connected?"
					end if
					
				end tell
			end if
		end tell
	end tell
end tell
