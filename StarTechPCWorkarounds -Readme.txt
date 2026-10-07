LowkFire USB Key outline

Immediately opens into root menu

-- Asks what environment you are currently in

	-- Options include Admin, WinRE, OOBE, and Exit
		-- Admin refers to cmd run as administrator AND preboot cmd
		-- WinRE includes all OfflineSystem cmd's
		-- OOBE usually refers to windows installment

After selection, moves into secondary menu

-- Menus include Admin, Preboot, WinRE, and OOBE

	-- Admin (:admin_main) menu inclusions:

		-- Make local user (:admin_makelocaluser)
		-- Make local administrator (:admin_makelocaladmin)
		-- Delete user (:admin_deleteuser)
		-- Force cmd preboot (:admin_cmdpreboot)
		-- Return

	-- WinRE (:winre_main) menu inclusions:

		-- Force cmd preboot (:winre_cmdpreboot)
		-- Delete user (:winre_deleteuser)

	-- OOBE (:oobe_main) menu inclusions:

		-- Bypass network requirement (:oobe_bypassnro)
		-- Immediately create local user (:oobe_createlocaluser)

--- ADMIN ---

::makelocaluser::
	Ask for username and password
	Create local user
	Display complete screen + pause
	Return to admin_main

::makelocaladmin::
	Ask for username and password
	-- Fail fallback if username left blank
	Add local user
	Add local user to administrators
	Diaplay complete screen + pause
	Return to admin_main











--- WinRE ---

::deleteuser::
	Ask for the desired user to delete
	Load HKLM\OfflineSAM\...\Users
	Find user in \Users\Names
	-- Fail fallback if username does not match any existing users
	Find default RID value
	Store default RID value
	Delete file in \Users\Names
	Delete file corresponding to user's RID in \Users
	Unload HKLM\OfflineSAM
	Ask "Clear all user files from drive?"
	Clear all user files if prompted
	
