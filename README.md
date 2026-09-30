How to run TruckDash on Linux under Proton for ETS2/ATS and TruckersMP as well.  For purposes of this guide, I will assume you have a native steam install, and have installed Proton-GE Latest using protonplus and have 7zip installed
$ refers to a command run in terminal
and a tilde or "~" refers to your home folder which when expanded would be /home/YOURUSER/

First let us set up TruckersMP, go to their website https://truckersmp.com/ and download the executable. 

Create a folder in your home directory for the install with mkdir -p ~/TruckersMP

Install Wine, ProtonPlus and Winetricks using your package manager (Arch Linux: sudo pacman -S wine winetricks protonplus 7zip)

In terminal type this command $ WINEPREFIX="/home/YOURUSER/TruckersMP/" wine "/home/Downloads/TruckersMP-Setup.exe" 

If where you downloaded the exe is different, substitute accordingly. also replace YOURUSER with your linux username. 

Let the terminal do it's thing until TruckersMP Launcher is installed and you are presented with the main menu. Then close the menu and that terminal.

For future reference, the app is now located at /home/YOURUSER/TruckersMP/drive_c/users/YOURUSER/AppData/Local/TruckersMP/TruckersMP-Launcher.exe

You will notice Wine has created Desktop shortcuts too, please remove them with 

rm -rf ~/.local/share/applications/wine/Programs/TruckersMP

In steam, add TruckersMP as a non steam game twice, using the path /home/YOURUSER/TruckersMP/drive_c/users/YOURUSER/AppData/Local/TruckersMP/TruckersMP-Launcher.exe

The first entry should be renamed TruckersMP (ATS), and the second entry TruckersMP (ETS2)

right click those non-steam games and click properties. 

launch options for the ATS version will be STEAM_COMPAT_DATA_PATH="/home/YOURUSER/.local/share/steam/steamapps/compatdata/270880" %command%
launch options for the ETS2 version will be STEAM_COMPAT_DATA_PATH="/home/YOURUSER/.local/share/steam/steamapps/compatdata/227300" %command%

both shall have forced compatibility to Proton-GE Latest

This essentially runs the TruckersMP launcher in ETS2 and ATS prefixes respectively allowing it to read both saves. 

when you open the TruckersMP launchers, you will need to specify the game paths for both ETS2 and ATS, please copy both below and paste into their fields, and replace YOURUSER with your linux username. 

Z:\home\YOURUSER\.local\share\Steam\steamapps\common\Euro Truck Simulator 2\
Z:\home\YOURUSER\.local\share\Steam\steamapps\common\American Truck Simulator\

additionally you can add -nointro to both console options.

Now we must set up TruckDash.exe

go to https://github.com/Nethercap/truck-companion and download the latest release

open terminal and run $ 7z x TruckDash-windows.zip to extract the executable. 
type in $ mkdir -p ~/truckdash
and then $ mv TruckDash.exe /home/YOURUSER/truckdash/

Now all we need is desktop entries for TruckDash for both ETS2 and ATS
go to the releases page of this repo and download the zip and extract with 7z in terminal and make sure to edit the .desktop files and replace YOURUSER with your linux username, yes repetition is boring but I have to be clear. 

[Desktop Entry]
Type=Application
Name=Truck Dash (ETS2)
Comment=Truck Dash client for Euro Truck Simulator 2 (start the game first)
Exec=env STEAM_COMPAT_DATA_PATH="/home/YOURUSER/.local/share/Steam/steamapps/compatdata/227300" STEAM_COMPAT_CLIENT_INSTALL_PATH="/home/YOURUSER/.local/share/Steam" "/home/YOURUSER/.local/share/Steam/compatibilitytools.d/Proton-GE Latest/proton" run "/home/YOURUSER/truckdash/TruckDash.exe"
Terminal=false
Categories=Game;
StartupNotify=false

[Desktop Entry]
Type=Application
Name=Truck Dash (ATS)
Comment=Truck Dash client for American Truck Simulator (start the game first)
Exec=env STEAM_COMPAT_DATA_PATH="/home/YOURUSER/.local/share/Steam/steamapps/compatdata/270880" STEAM_COMPAT_CLIENT_INSTALL_PATH="/home/YOURUSER/.local/share/Steam" "/home/YOURUSER/.local/share/Steam/compatibilitytools.d/Proton-GE Latest/proton" run "/home/YOURUSER/truckdash/TruckDash.exe"
Terminal=false
Categories=Game;
StartupNotify=false

in terminal $ chmod +x truckdash-*
in terminal $ cp -a truckdash-* /home/YOURUSER/.local/share/applications/ 
and then $ cp -a truckdash-* /home/YOURUSER/Desktop/

those three commands just made the .desktop entries executable, and copied to your applications folder and Desktop. 

side note the "/home/YOURUSER/.local/share/Steam/compatibilitytools.d/Proton-GE Latest/proton" is where Proton-GE is installed.
your normal Protons or Proton-Experimental will be in "/home/YOURUSER/.local/share/steam/steamapps/common/Proton - Experimental/proton"

Order of Operations to get Truck Dash running in Singleplayer

Run ETS2 or ATS, then run TruckDash (ETS2) or TruckDash (ATS)

Order of Operations to get Truck Dash running in TruckersMP

Run TruckersMP (ETS2) or TruckersMP (ATS), then run ETS2 or ATS within those launchers and then run TruckDash (ETS2) or TruckDash (ATS
