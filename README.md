Heyo it's Markus/A Dude, this ReadMe aims to explain and tutorialize how to edit the Community Server files here in this repository.
I've sectioned things in the followng chapters:

1. How Server Files Work
2. Managing GameMode Rotation (Mods included)
3. Using GitHub Desktop

‎ 
‎ 


#  **1. How Server Files Work:**

In the ED directory, inside the "data" folder, there are three main folders pertaining to the gamemode rotation in a server:

"server", "map_variants" and "game_variants"
<img width="1173" height="329" alt="image" src="https://github.com/user-attachments/assets/a011ef6f-3686-4e88-ad54-841020fa6aa6" />

‎ 

"server" contains text files that actively control the rotation. These files must be open with code editing software, it is highly reccomended to download either notepad++ or VSC (Visual Studio Code).
<img width="1173" height="276" alt="image" src="https://github.com/user-attachments/assets/6d32bea2-3a34-4ffc-a726-7b95b9a8b082" />

‎ 

"map_variants" and "game_variants"  list all map and game variant files, respectively. Each file is stored in its own folder, which should be clearly named after the corresponding map or variant (as named in game on custom game menu). These ED-specific files are typically named "sandbox.map" or "variant.koth". Be careful not to place these files in the wrong folders, as mixing them up can cause a lot of confusion when setting up the server rotation.
<img width="1160" height="280" alt="image" src="https://github.com/user-attachments/assets/8bbd435c-3bda-412b-94e7-eeef05e493ba" />
<img width="1158" height="795" alt="image" src="https://github.com/user-attachments/assets/9445685c-55de-421e-a469-efb699a03390" />


‎ 
‎ 

#  **2. Managing GameMode Rotation (Mods included):**

The GameMode rotation on a server is primarily controlled by the "voting.json" file. At the beginning of this file, you’ll find a "maps" section that defines the initial set of core maps (such as Valhalla, Standoff, etc.). After this section, each GameMode is added under the "types" section, using the following format:

```
{
      "displayName": "Castle Wars",
      "typeName": "Castle Wars",
      "modPack": "Customization++",
	  "minPlayersAllowed": 1,
	  "maxPlayersAllowed": 16,
	  "commands": [
        "Server.Sprint 1",
        "Server.UnlimitedSprint 1",
        "Server.AssassinationEnabled 0",
        "Server.TeamSize 1",
        "Server.PodiumEnabled 0",
        "Server.EmotesEnabled 1",
        "Server.EmotesDuringPodiumEnabled 1",
        "Server.KillCommandEnabled 1",
        "Server.KillCommandDuringPodiumEnabled 1",
		"Server.NumberOfTeams 2",
		"Voting.ReloadJson",
		"Time.GameSpeed 1",
		"Voting.ReloadJson"
      ],
      "specificMaps": [
		{
          "displayName": "Tundra Wars",
          "mapName": "Tundra Wars"
        },
        {
          "displayName": "Ruined Castle",
          "mapName": "Ruined Castle"
        },
        {
          "displayName": "Rainbow Castle",
          "mapName": "Rainbow Castle"
        }
		]
  }
```

Below are descriptions for each significant line in this format, in order:

``` "displayName" ``` Variant name exhibited in the voting screen (Big Bold text)

``` "typeName" ``` Folder name in the "game_variant" folder

``` "modPack" ``` Mod name, should be in accordance to name defined in "mods.json" file

``` "minPlayersAllowed" ``` Minimum player count where GameMode is allowed in rotation (PlayerCount ≥ Minimum)

``` "maxPlayersAllowed" ``` Maximum player count where GameMode is allowed in rotation (PlayerCount ≤ Maximum)

``` "commands" ``` Any console command to be executed before the GameMode starts.

``` "specificMaps" ``` List of maps that the variant (typeName) can cycle through in the rotation

``` "displayName" ``` Map name exhibited in the voting screen (Smaller text)

``` "mapName" ``` Folder name in the "map_variant" folder

‎ 

If including more than one GameMode, you will need to add commas to the end bracket for each GameMode inserted before the last one, and also make sure there is an end bracket for each start bracket. This rule extends to the brackets within the "specificMaps" brackets.


As a failsafe for this, i highly recommend using the following site to validate your .json file before submitting your changes in a commit: https://jsonlint.com
<img width="1450" height="790" alt="image" src="https://github.com/user-attachments/assets/6be8200e-4e26-469e-8ba7-e47c78ba4aec" />

‎ 
‎ 
The "modPack" name utilized in the "voting.json" must comply with the one used in the format as seen below in the "mods.json" file:

```
{
  "mods": {
    "Customization++": {
      "package_url": "http://www.files.halobase.box.ca:15771/api/public/dl/USAMzEw5/Mods/Twisted%20Flog/Customization%2B%2B.pak"
    },
    "PlayerRepParty": {
      "package_url": "http://www.files.halobase.box.ca:15771/api/public/dl/P83Q8NiA/Mods/Enash/PlayerRepParty.pak"
	}
  }
}
```

‎ 

The download links, as seen in the example above, were given by ED discord moderators and modders. Unless available from another source (currently you can use the Dewrito Share  site https://fileshare.zgaf.io), I reccomend consulting those people if you're looking for download links to any mods.


‎ 
‎ 


#  **3. Using GitHub Desktop:**

I'm assuming, much like me, most people haven't used GitHub at all. So as a first, here's a basic ass explanatory text about how it generally works:


> This repository (this folder of files) is made public so that anyone may see it, and by contacting me I'll add your account to the author list which will make you able to edit these files. 


> How that editing is done is by way of sending "commits" to the repository. With the GitHub Desktop app you'll locally download the repository files, allowing you to change them as you see fit, the app will automatically recognize all these changes and group them up in a "commit".


> The way you can make those changes affect the main repository is by "pushing" the commit. So once that commit has been pushed to the main repository, the files will have been updated, prompting every other user to "pull" those new files so that they re-download the files in the new up to date version of the repository.

‎ 
‎ 


As a first, make sure to create a GitHub account and download GitHub Desktop, linking it to your account. The application will look something like the image below:
<img width="1649" height="1020" alt="image" src="https://github.com/user-attachments/assets/07c24368-0470-41fc-b221-da72281a1210" />


After loging in and having linked the account in the GitHub Desktop app you will need to download this repository to you local PC storage. Clicking on the "File" tab up top, then on "Clone Repository..." you must only fill in the Repository URL with the following link: 


Once that is done, choose a folder in your local PC to house these repository files.


At this point, the editing process is fully functional, no need to set-up anything else. The only thing to keep in mind when making changes is the following procedure:
1. Open GitHub Desktop
2. Fetch Origin (To refresh local files)
3. Make changes
4. Appropriately Name and write the description of the changes in your commit
5. Send Commit to main fork

That's all really. Any and all communication in regards to server files are to be done externally, aka. most likely one of the ED discords. If anything major happens in terms of upkeep or moderation of these server files, please do contact me (Markus/A Dude on discord) (I'll probably know about it, but user feedback always gives better insight into the problem).


