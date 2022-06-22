# beamleague
A repository for a beamng private server
How to Install
For installation instructions, please see server installation.

The ServerConfig File
The server config, which is a file called ServerConfig.toml, uses the TOML format. (NOTE: The old server config file was called Server.cfg, but this is no longer used, and the server will warn when this is still present. Please also note that the two config formats are not compatible with each other.)

The config has one section by default, called [General], which holds the following values:
 

Key	Value Type	Description
AuthKey	
AuthKey format ‘xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx’

where all x's are alphanumeric characters (numbers and letters). 

Used to identify your server with the backend. You should have gotten one while following the installation instructions.
Debug	true / false	When enabled (true), will show more messages in the log and provide more information. Enable this if you run into issues. Enabling this will drastically increase the size of the log file.
Private	true / false	When enabled (true), your server will not be shown in the server list. Anyone with the correct IP and port can still connect.
Description	Any "text"	Shown as the description of the server in the server list (if the server is public). You can use special characters to format this with colors and styles.
Name	Any “text”	Shown as the name / title of your server in the server list. You can use special characters to format this with colors and styles.
Map	A valid map location, such as '/levels/gridmap_v2/info.json'	The map your server will host. Has to be installed either by default (a list can be found below) or as a server mod.
MaxCars	Any number ≥ 1	The maximum number of cars per player. Any additional cars a player tries to spawn will be deleted instantly.
Port	1024–65535	The networking port on which the server will be accessible. For a player to connect to your server directly, they will need your IP and this port.
Other sections can and should be used by server plugins (Lua API coming soon), like so: [MyMod].

The AuthKey HAS to be set by you. It will be empty by default, and needs to be filled with your AuthKey from the installation step earlier. Do not share this Key with anyone and, in screenshots, blur it fully.

All Vanilla Maps Names
Here are all the stock maps 

/levels/gridmap_v2/info.json
/levels/automation_test_track/info.json
/levels/east_coast_usa/info.json
/levels/hirochi_raceway/info.json
/levels/italy/info.json
/levels/jungle_rock_island/info.json
/levels/industrial/info.json
/levels/small_island/info.json
/levels/smallgrid/info.json
/levels/utah/info.json
/levels/west_coast_usa/info.json
/levels/driver_training/info.json
/levels/derby/info.json
Customize the look of your server name
Use these special symbols before your text and it'll apply an effect to that text in the server list
 

^r	reset
^p	newline (descriptions only)
^n	underline
^l	bold
^m	strike-through
^o	italic
^0	black
^1	blue
^2	green
^3	light blue
^4	red
^5	pink
^6	orange
^7	grey
^8	dark grey
^9	light purple
^a	light green
^b	light blue
^c	dark orange
^d	light pink
^e	yellow
^f	white
The Server.log file
This file will be generated when the server runs. It's a mirror of the messages you see in the console when you run the server. You should attach this file every time you need support from our support staff, and it will never show your AuthKey, so you can usually send it without modifications.

The format is as follows ($ prefix means “variable”, explained below):
 

[$DATE $TIME] $CONTEXT [$LOG_LEVEL] $MESSAGE
Where:

$DATE is the date of the message, for example 21/07/2021
$TIME is the time of the message, for example 11:05:23
$CONTEXT (only visible if in Debug mode and mostly relevant to developers) is the context of the message, which is either:
(Player ID) “Player Name”, where the Player's ID is useful for moderation
A short name such as “HeartbeatThread”
$LOG_LEVEL is one of the levels of importance of a message:
DEBUG: Only visible in Debug mode, usually spammy and only important to developers
INFO: General information
LUA: Message from a Lua plugin
WARN: Describes something that isn't supposed to happen, usually
ERROR: Something went very wrong, or was very unexpected
FATAL: Something happened that causes the server to shut down
$MESSAGE the message itself, usually something that you should pay attention to and understand. In some cases this might be cryptic, but the general rule is that, as long as nothing is visibly wrong with the server and there are no ERRORs, all is good.
Updating The Server
Why to Update
Whenever a new update is released, you're advised to update your server. Usually this involves bug fixes, stability improvements and security improvements, next to the general new features etc. that are introduced.

To receive news about updates when they come out, either follow the discord server's “update” channel, look out for it on the forums, or look at / ask the GitHub releases page.

How to Update
The server is updated by replacing the old executable with the new one. If you are unsure how to do this, there are step-by-step instructions for Windows and Linux below.

If you built from source, you just rebuild. Make sure to run git submodule update --init --recursive before you rebuild.

On Windows
Go to BeamMP.com and click the “Download Server” button.
Once downloaded, extract the zip file. You should see a few files, one of them the BeamMP-Server.exe. We will call this one the “new executable”.
Go to the folder where your current BeamMP-Server.exe executable is located (same folder where your ServerConfig.toml is, usually). We will call this one the “old executable”.
Replace the old executable with the new executable (for example by copying or moving the new executable into the folder).
On Linux
Go to BeamMP.com and click the “Download Server” button.
Once downloaded, extract the zip file. You should see a few files, one of them the BeamMP-Server-linux. We will call this one the “new executable”.
Go to the folder where your current BeamMP-Server-linux executable is located (same folder where your ServerConfig.toml is, usually). We will call this one the “old executable”.
Replace the old executable with the new executable (for example by copying or moving the new executable into the folder).
Open a terminal in that folder where you just replaced the executable, and run sudo chmod +x BeamMP-Server-linux. This will make sure the server can be run.
Automated Updates
The server does not support automatic updates or update notifications (yet).

You can, however, ask the GitHub API for the lastest release by checking the server's version against the tags. You can get that by GET'ing from https://api.github.com/repos/BeamMP/BeamMP-Server/git/refs/tags.
