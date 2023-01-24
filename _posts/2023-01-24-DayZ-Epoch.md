---
layout: post
title: Arma2 and Dayz-Epochmod
date: 2023-01-24 15:00
description: Reliving old times and playing with the latest DayZ Epochmod on a private server
comments: true
toc: true
tags:
 - PC
 - Linux
 - Windows
 - Games
---

The first time I ever came across Dayzmod was browsing Youtube and happened to land on the wonderful `FrankieonPCin1080p`. I'm not gonna go into what has happened but will just tell you find his channel and watch the fantastic vids he has put up and then go look for others.


The bulk of this guide came from [RobbieW69](https://github.com/RobbieW69), I've edited and changed a few parts but the bulk of it came from his repo and [video on youtube](https://www.youtube.com/watch?v=SuIGpzAtU0Y) Star, Subscribe and follow him.

---
# Assumptions
You have ESXi installed on a host.
You have already installed Windows (any version) into a Virtual Machine.
You have administraitive rights.
The virtual machine is reachable by remote desktop and has file sharing enabled and working.
You have Arma2, Arma2 Operation Arrowhead and have all the DLC.
You know how to add a mod to Arma2

---
# Preparing Arma & Epoch
* Verify Integrity of the Game Files (Right Click on the Game(s) in your Library -> Properties -> Local Files -> Verify integrity of game files). Run Arma 2 until the main menu, then close it, and run OA till main menu then close it. Locate your steam library, Find the `common` folder within `steamapps` Right click and Share this folder. Now log on to the VM and ensure you can browse to this share.

From here onwards everything will be done in the virtual machine.

* Download and install [DayZ Launcher](http://app.dayzlauncher.com/updates/setup_dzlauncher.exe), After DayZ Launcher has installed, Launch it and Open the Settings Panel (Top Right). Set the `Mods/Downloads Path` to your Arma 2 OA Install Directory (Example. `C:\Program Files (x86)\Steam\steamapps\common\Arma 2 Operation Arrowhead`). And Set the `Arma 2 Path` to your Arma 2 (Base Game, NOT OA!) Install Directory (Example. `C:\Program Files (x86)\Steam\steamapps\common\Arma 2`).Scroll down and hit `Save` then close the Settings Panel, and Navigate to the `Mods` Tab in DayZ Launcher. Find `DayZ Epoch 1.0.7` In the Mods List, and Click Download. Once the Mod has finished downloading, be sure to Verify the Install by Clicking the Verify Button

* Download [Epoch 1.0.7 Server Files](https://drive.google.com/file/d/1jDn86sfTwcRae4NZgHK76k_CaY1jOUP2/view)


## Installing MySQL Server & Workbench (Database)
* Download [MySQL Server](https://dev.mysql.com/downloads/file/?id=508935). Download the one that has the smallest size, once it has downloaded, run the Installer. Select the `Server only` Setup Type, Click Next and then Execute, you might have to install some Redistributables during this process. Follow the Installer Process until you reach the `Product Configuration` Section, Press Next Once, and you should come to the `Type and Networking` Page.

* Installing MySQL Server & Workbench can be confusing to those with little to no experience, particularly this next Section, so please read carefully. 
The `Config Type` Option: If you are planning to Host this Server on a Home Machine, you can leave the Settings on this Page as they are and click Next. If you are Hosting from a (relatively decent) Dedicated Server Machine, select `Server Computer`, and leave the rest of the options as they are and click Next. `Authentication Method`: Set this to `Use Legacy Authentication Method`
`Accounts and Roles`: MySQL has a "root" User Account, which is a user that has full priviledges on the Server, so be sure to set the Root Password to be strong and secure, keep a note of it if you need to. You May Add & Configure MySQL Users on this Page if you wish to do so, for the sake of simplicity for this Guide, we will not run over this. Click Next. The `Windows Service` Page: Leave this Page as it is, and click Next, and Click Execute on the Next Page, the Finish the Installation.

* Download MySQL Workbench [here](https://dev.mysql.com/downloads/file/?id=507335) and run the Installer. Follow the Installer, select the `Complete` Setup Type, press Next, then Install, once the Install has Completed, Launch MySQL Workbench. Click on the `Local instance MySQL80` Box, enter your Root Account password you set earlier. You should now be presented with a fairly confusing looking screen, if that is the case, then you can Minimize MySQL Workbench for now, we will continue here in a little while.

* Download and Install [PBO Manager](https://drive.google.com/file/d/1V_ivuaVIkDJuqULvhwAfbEtlp45eOE-X/view?usp=sharing), to make sure your PBO Manager was installed correctly go to Windows Settings -> type "defaults" -> Default Apps -> Choose default apps by file type -> Scroll down to '.pbo' on the left and make sure PBO Manager is the application assigned to it. You should see the icon next to PBO files now.

* Download and install [WinRAR](https://www.win-rar.com/fileadmin/winrar-versions/winrar/th/winrar-x64-602.exe) or [7 Zip](https://www.7-zip.org/a/7z2106-x64.exe)

* Download and install [Visual Studio Code](https://code.visualstudio.com/docs/?dv=win) and [Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.1.9.3/npp.8.1.9.3.Installer.x64.exe) we will be using both!

* Download the [Setup Guide Files folder](https://drive.google.com/drive/folders/1ln5BWdNLfw1AcWfyHHCORErb2O-bQwIo) from the google drive to follow along with.


---
# Server Install and Setup

I'm having you name files and folders certain things only so you can follow along easier, you can name them whatever you want please just remember when editing Directory names to change them to what you make them.
## Steps
- 1: Open File Explorer -> Make a folder anywhere call it `DayZ_Server`.

- 2: Open Arma2:OA directory via the file share you made earlier -> Copy everything in there into `DayZ_Server`. 
 
- 3: Open Arma2 Directory via the file share you made earlier -> Copy `AddOns` folder only to `DayZ_Server`.
 
- 4: Open File Explorer -> Make another folder not in the same Drive called `DayZ_Server_Config`.
 
- 5: Open Epoch Server Files -> Move the `DZE_Server_Config` into the `DayZ_Server_Config` folder you made.
 
- 6: Move all other Epoch Server Files into the `DayZ_Server` folder we made. `arma2oaserver.exe` should be in this folder. 

- 7: Open HeidiSQL -> Make a new Session, call it `DayZServer`. 
  - Sign into the 'root' with the password you made on MySQL 5.7 -> right click on `DayZServer` at the top -> Create new -> database ->name it like `dayz_db` -> for Collation find the one called `utf8_general_ci` -> Create.
  - Now a database named `dayz_db` should have popped up inside the drop down next to like `mysql` and `information_schema`. Click on it -> Over on the right side toward the top you'll see a blue button that says Query, click it -> a new empty window popped up -> Open `DayZ_Server`  folder -> find `SQL` folder -> open it, now drag `epoch.sql` into that area where the Query opened. Next to the Query tab it will say 'Database:dayz_db', ABOVE that there is a blue Play button, click it after putting the 'epoch.sql' file into the Query.
  - Now a dialog should have popped up saying `produced 1 warning`, ignore it.Now that next to where that Query tab was -> Click on that little gray window with the little green plus sign -> This opens a new Query tab -> Drop the 'add_recommended_mysql_events.sql' in that one and run it as well.Now a dialog should have popped up saying `produced 7 warnings`, ignore it.
  - Click on ‘dayz_db’ while in Heidi, click on the people icon, now under User Management click the green Add button, it will prompt you to make a new user I would name it something like “newServer” or whatever you want, make a good password, then toward the bottom of that same dialog it says “Allow access to”, click the green ‘Add object’ button, click on ‘dayz_db’, then when it goes into the list below, click on the checkbox next to it, do not click on checkbox next to ‘global privileges’ only the one next to ‘dayz_db’.
  - Now navigate to the `HiveExt.ini` located in your `DZE_Server_Config` folder, go down to line 36, change the `database = ` to `database = dayz_db` then below that change `Username` equal to `newServer`, then below that change the password to the password you set. 

- 8: Open Visual Studio Code -> Navigate to the top left -> blocks icon called 'Extensions' -> type `SQF` -> Install `SQF Language` by Vladislav and `SQFLint` by Skace.
  - Open File Explorer -> Open `DayZ_Server\@DayZ_Epoch_Server\addons` -> Right click on `dayz_server.pbo` -> PBO Manager -> `Extract to dayz_server\`. 
  - Now drag the `dayz_server` folder into the Workspace as well -> Trust -> Add to workspace.
  - Now go back to `DayZ_Server\MPMissions` ->  right click on `DayZ_Epoch_11.Chernarus` -> PBO Manager -> `Pack into DayZ_Epoch_11.Chernarus.pbo`. 
  - Now drag the `DayZ_Epoch_11.Chernarus` folder into VS Code on left side under `Workspace` -> Trust -> Add folder to workspace.    
  - Now find the `DayZ_Server_Config` you made -> open it -> drag the `DZE_Server_Config` folder into the workspace as well. 
  - Now at the top click File -> Save Workspace As -> Name it something like `DayZ Code` -> Save it to your desktop. Now click File again and click on Auto Save. You are now done    setting up the text editor. (remember to drag the `folders` not the `.pbo` files into VS code)

- 9: In VS Code -> In the worksapce -> click on `DZE_Server_Config` -> Click the arrow to open it -> go to `11_chernarus.bat`. 
   - Change the Directories to yours. (ie: '`-config=C:\DZE_Server_Config\11_chernarus.cfg`' will change to '`-config=YourDrive\DayZ_Server_Config\DZE_Server_Config\11_chernarus.cfg`'). 
   - Now open the `11_chernarus.cfg` -> change 'hostname = ;' to whatever you want to name it, this will be what pops up on the server list, below that you can also have a server password.

- 10: Open -> `DZE_Server_Config` -> put the 'start.bat' inside.Change the directories in the `Start.bat` before you start it. 
  - In VS Code -> Top left click 'Terminal' -> New Terminal -> a drop down menu will pop up -> click on `DZE_Server_Config` -> the new terminal window will have opened up at the bottom -> type `start start`. 
  - Your server should start up. If you make changes in VS Code while the server is up, once you are ready to restart -> close the server -> then click on the Terminal window toward the bottom -> You should be able to just hit the Up arrow key or type 'start start' again.

***Debugging: If you have any problems with the server -> go to `DZE_Server_Config` -> `arma2oaserver.RPT` is where your logs and errors will be 90% of the time. If you have problems on the Client side -> Open File Explorer -> At the top in the address bar type `%appdata%` -> Go back one folder and click 'Local' -> Arma 2 OA -> 'ArmA2OA.RPT'.
If it has an error that  says `Include file z\addons\dayz_code\gui\description.hpp not found` -> go to the `11_chernarus.cfg` and change the name to something like `TEST` -> then go to `11_chernarus.bat` then check all your spelling and directory changes, this error is typically due to the server not actually being directed to the Mission folder, the other possible problem is that you do no have a `$PREFIX$` file in your `@DayZ_Epoch_Server\addons\dayz_server` folder. After putting `TEST` in the name, restart the server and see if the server name changes, if not, go to `11_chernarus.cfg` and check the line that says ```template = “DayZ_Epoch_11.Chernarus”;``` and make sure it is directed to the correct folder.***


Your server should run and not have any problems now, if it does not start please refer to ++Debugging++, if you are ready we will move on to editing your server, click below to return to the ReadMe.

---
# Editing your new Epoch Server
If you've made it this far and succesfully loaded into your own server, congrats! Now it's time to start modding it to fit what you want.But before you do that I HIGHLY recommend making backups of your "@DayZ_Epoch_Server" and your "MPMissions"  folder regularly. I'm going to add some simple mods to get you started.
## Making Edits
* Before adding mods, you should go navigate to `DZE_Server_Config\BattleEye\scripts.txt`and change all the `5`s to `1`, this where Notepad++ comes in handy. 
* Open the `scripts.txt` in VS Code, Ctrl + A, then Ctrl + C, now open up Notepad++ and hit Ctrl + V, everything in `scripts.txt` should be pasted into Notepad++. 
* Now, In Notepad++ at the top there will be a bunch of icons, all the way to the right there is a Circle icon, it says `start recording` when you hover over it, go ahead and click it, once you do it will become unclickable. 
* Now go to line 2 -> begins with `5 addAction`, click anywhere on that line, now hit the Home key on your keyboard, now hit the Right arrow key, Backspace, type `1`, then Down arrow key. Once you’ve done this go back to the top and hit the Square button right next to the Circle button we pressed earlier to `Stop Recording`. 
* Now to the right of them there is a Triangle Play button, you can click this 83 times, or you can click the double triangle play button, a dialog will come up asking how many time you want to run the macro you just created, I believe its 83, type `83` into the box, click run. 
* Scroll down and make sure all of them were set to `1`, if any were missed go ahead and change them. 
* Now go ahead and Ctrl + A, Ctrl + C, then navigate back to VS Code, and Ctrl + V (unless you closed it then you will need to highlight everything in the `scripts.txt` file that you have open in VS Code again before pasting into it. 
* After making edits or addings mods to the server, remember in order to start server you type the 'start start' command in the terminal in VS Code, as the 'Start.bat' will repack your PBO's for you. 
* If this is going to be a private server and you don't need the security -> go to '11_chernarus.cfg' -> find line 'BattlEye = 1;' then set to 0, also find the line  `password = “”;` and make a good one!, if so you don’t need to follow the [Battle Eye Filters](../writeup/BattleEye.md), after installing the Admin Tools you are good to go!

## Value Edits
* Open File Explorer -> `DayZ_Server\@DayZ_Epoch\addons` -> right click `dayz_code.pbo` -> PBO Manager -> `Extract to dayz_code\` -> drag the `dayz_code` folder into the VS Workspace -> Add to Workspace. 
* Open it in the workspace -> find `configVariables.sqf` -> right click -> Copy. 
* Navigate to your `DayZ_Epoch_11.Chernarus` folder in the workspace -> if you don't already have a folder there called `dayz_code`, make it then ->right click -> Paste (or Ctrl + V). 
* Now, while in that folder still -> right click on it -> New Folder -> name it `init`. Now go back to the `dayz_code` folder -> init -> find `variables.sqf` -> right click -> Copy. 
* Navigate back to the `DayZ_Epoch_11.Chernarus` folder and go to the empty `init` folder you made -> Right click -> Paste. Right click on the `dayz_code` folder in the workspace -> Remove folder from workspace. 
* Now go back to `DayZ_Epoch_11.Chernarus` folder and click on `init.SQF`. Find this:
```ruby
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";
```
and right BELOW it put:
```ruby
call compile preprocessFileLineNumbers "dayz_code\init\variables.sqf";
call compile preprocessFileLineNumbers "dayz_code\configVariables.sqf";
```
* Now to make the value edits you would like, you'll be editing `init.sqf`, `configVariables.sqf`, and `variables.sqf`. 
* If you want ZSC single currency for example, enable it in the `configVariables.sqf` by changing:
```ruby
Z_SingleCurrency = false;
```
to 
```ruby
Z_SingleCurrency = true;
```
* Go to `Description.ext` in your mission folder -> at the bottom find:
```
#include "\z\addons\dayz_code\Configs\CfgServerTrader\CfgServerTrader.hpp" // Normal traders
//#include "\z\addons\dayz_code\Configs\CfgServerTraderZSC\CfgServerTrader.hpp" // Single currency traders
```
and change to:  
```
//#include "\z\addons\dayz_code\Configs\CfgServerTrader\CfgServerTrader.hpp" // Normal traders
#include "\z\addons\dayz_code\Configs\CfgServerTraderZSC\CfgServerTrader.hpp" // Single currency traders
```
## Map Addons
* We're going to add custom map addons server side, watch my [video](https://youtu.be/y639xY7ekdc) on how to make your map edits.
* Navigate to `dayz_server` in your workspace -> Right click -> Add new File -> name it `build.sqf` -> Add New Folder -> Name it `custom_buildings` -> grab your `mission.sqf` file from the map edit you did -> rename it to like `BalotaAddons.sqf`  for example if you made changes to Balota -> now place that file in the `custom_buildings` folder. 
* Navigate to `dayz_server\init\server_functions.sqf` -> find:
```ruby
call compile preprocessFileLineNumbers "\z\addons\dayz_code\loot\init.sqf";
 ```
then right BELOW it add:  
```
#include "\z\addons\dayz_server\build.sqf";//build custom map addons before player setup
```
* Now go to the `build.sqf` script and type: 
```ruby
execVM "\z\addons\dayz_server\custom_buildings\BalotaAddons.sqf";
```
Restart your server and the map edits you made will work.

## Third Party Mods
I use the following mods
 [Wicked AI](https://github.com/worldwidesorrow/WICKED-AI) The Install guide is on the main repo page, just scroll down.
 [DZAI](https://github.com/SnarkIndustries/DZAI) Use [this guide](https://github.com/SnarkIndustries/DZAI/blob/master/Installation%20Guides/2.%20Install%20Instructions%20-%20dayz_server.pbo%20installation%20(PBOManager).txt) to get things going.
 [DZMS](https://github.com/SMVampire/DZMS-DayZMissionSystem) The install guide is on the main repo page.

To begin with I'd advise you just go with WAI, For the most part this will be all you need. I use the others to just compliment things in that the missons from DZMS are slightly basic but enables you to have more activity on the server. If you do end up making a public server ensure that you check over things regularly and if having multiple AI causes your bill to increase then drop DZAI and just have WAI and DZMS.

* Most 3rd party mods from github have a `readme.md` that you can follow, the good ones give you the battleye exceptions you need as well, but if you add a mod that doesn't give you the battleye exceptions you will want to run 'BE_AEG.exe' if the kicks are due to 'script restriction' and any other filter .txt file restrictions you will have to add manually, this gets covered later in the `Battle Eye Filters` section.

## Installing the Admin Tools
BigEgg made some great [Anti Hack Admin Tools](https://github.com/BigEgg17/Epoch-Antihack-Admin-Tools) for the community to use and they work on Epoch 1.0.7! They let admins fly, teleport, and overall do what they need to do.
* You will want to follow the `readme.md` on the github for the installation of the admin tools until you get to `Step 11: Drag all the BattlEye filters from the BattlEye folder into your server's BattlEye folder.`, do not do that, instead come back and continue.

You are now done learning how to edit your server.

---
# Making Battle Eye Exceptions
BattleEye reads filters from the `.txt` files inside the folder, it then reads everything after the function name, for example in `DZE_Server_Config\BattleEye\scripts.txt` line 40 says `1 execVM` , 1 being the filter style and `execVM` being the function, everything after are the Exceptions. Exceptions allow someone to execute that function in a certain way without being kicked by BattleEye. Please read the [Battle Eye Filters Guide](https://github.com/AsYetUntitled/Framework/wiki/BattlEye-Filters) to get a better understanding then come back.

## Generating Restrictions
If you followed the 'Making Edits' in [this](../main/EditingTheServer.md) then you should have all of your filters inside the `DZE_Server_Config\BattleEye\scripts.txt`set to `1`'s. 
* Go ahead and launch theserver and the game and join the server and when you get in, press F2 and do everything the admin menu allows you to. This will generate the restrictions(kicks) that would normally happen.
* Once you are done testing every admin tool available, close the server. (which means spawn everything, teleport, ect. everything)
* If you navigate to `DZE_Server_Config\Battle` you will notice a new file called `scripts.log` , this is filled with all the restrictions we've just generated. When a mod tries to call one of the Functions but does not have an Exception for it, BattleEye will kick the user. It will then note this in `scripts.log` with the exact code that tried to call the function in quotes, along with the filter number.

## Generating Exceptions for Restrictions
* First let's open the Setup Guide Files folder we downloaded -> copy the `BE_AEG.exe` and the `with console debug.bat` into your BattleEye folder.
* Now, we need to generate Exceptions for the restrictions that were created by the Admin Tools (because flying and teleporting ect, do not have exceptions by default). But when we look at `scripts.log` we only need to look at the Restrictions that contain a random line(variable) of letters and numbers, for example 
```sql 
#79 "] call BQ1vBKUInpSNuc;
			};
		};

		if (-1 > -1) then {setViewDistance -1};
		if (25 > -1) then {setTerrainGrid 25};
		if (true"
```
with `BQ1vBKUInpSNuc` being the random variable and `setViewDistance` being the function.
* The reason we are only looking at and making exceptions for them is because the Admin Tools generates new variables every time the server starts again, so we have to add manual exceptions that will cover the code around them. All of the other restrictions should be fixed when we run the `BE_AEG.exe` by double clicking the `with console debug.bat` file. 
* In order to fix this we need to make an exception that gets as much of the code as possible but also removing the variable. If you followed the [Battle Eye Filters Guide](https://github.com/AsYetUntitled/Framework/wiki/BattlEye-Filters) you know we need to break this down so let's do it.
``` sql
 "] call BQ1vBKUInpSNuc;
 ```
 * Contains the problem variable. So let's start making the exception after it. Like this:
 ``` sql
  !"};\n };\n\n if (-1 > -1) then {setViewDistance -1};\n if (25 > -1) then {setTerrainGrid 25};\n if (true"
```
* So we head to `scripts.txt` and find line 79, we then go up two to line 81 because the filters don't start on line 1, it says `//new2` and the first filter `1 addAction` is 0, in programming numbers don't start at 1, they start at 0. 
* So now line 81 says `1 setViewDistance` and since that is the Function being called in the code, we know we are right, click on the line, hit the End key on your keyboard, and copy the exception to the end of the line. 
* Now we know how to make exceptions for the Admin Tools random variable restrictions. Please continue to find as many as you can with the random variables and fix them. Once you are done fixing them, navigate to your Battle Eye folder and double click on `with console debug.bat` and it will then auto generate the exceptions needed for all of the other `scripts.txt` restrictions. Then you should be good to go!

Restart your game and Server and rejoin, then leave, and check `scripts.log`, if it is not there, you are done. 

If you want more how about you consider upgrading to Epoch 1.7.0.1, it really is a simple import of SQL but I'll let you figure it out.


If you need help, please join the [Epoch discord server: https://discord.gg/0k4ynDDCsnMzkxk7](https://discord.gg/0k4ynDDCsnMzkxk7)


Share this guide with whoever you like.


`PLEASE NOTE I CANNOT GUARANTEE THE ABOVE GUIDE WORKS IN FULL AS THINGS CHANGE, AT THE TIME I WROTE THIS IT WORKED FOR ME`