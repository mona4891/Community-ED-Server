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


> This official repository (this folder of files) is made public so that anyone may see it. You will clone this repository locally to your computer and create a copy of them so that you may edit those local files. By editing this copy, you will have the option to request your changes be made to the official repository. You will do that by creating a Pull Request, which will be reviewd by me (to check for errors/bitcoin miners) before accepted and merged into the main repository, applying your changes to the server files.


> How you will edit the server files is primerily through the GitHub Desktop app. If this is your first time using it, this chapter is especifically designed for you to follow. As an abstract to what that all entails, here's all the steps you will take:
> 1. You will log in to your GitHub account
> 2. You will clone the repository files (URL: https://github.com/A-Dude101/Community-ED-Server)
> 3. You will create a "fork" (a copy) of that repository, where you will be making all your changes.
> 4. You will open a "Pull Request" to merge your changes with the official repository.
> 5. I will review the changes and then merge them. Making your changes officially applied to the server being hosted.

‎ Here follows a more detailed tutorial with images. I highly suggest you follow it step by step.
‎ 


As a first, make sure to create a GitHub account and download GitHub Desktop, linking it to your account. The application will look something like the image below:
<img width="1649" height="1020" alt="image" src="https://github.com/user-attachments/assets/07c24368-0470-41fc-b221-da72281a1210" />


After loging in and having linked the account in the GitHub Desktop app you will need to clone this repository to you local PC storage. Clicking on the "File" tab up top, then on "Clone Repository..." you must only fill in the Repository URL with the following link: https://github.com/A-Dude101/Community-ED-Server
Once that is done, choose a folder in your local PC to house these repository files (it must be an empty folder)

<img width="745" height="436" alt="image" src="https://github.com/user-attachments/assets/1073cc4b-9b5e-4076-b221-63b6c5f789db" />




At this point, the editing process is fully functional. All changes you make will be recognized and grouped up in an action called "commit". But the problem is that you are not able to edit the official repository files, you will need to make a copy of them (a "fork") so that you can apply those changes to your copy (your "fork").

For now, make any changes at all so that you are prompted to "create a fork", as seen below.
<img width="957" height="658" alt="image" src="https://github.com/user-attachments/assets/8558bd49-7a90-44b1-91ac-31e32b037f36" />



Click on the "create a fork" text and you will be prompted "Do you want to fork this repository?", as seen in the image below. Continue by clicking the option "Fork this repository".
<img width="954" height="661" alt="image" src="https://github.com/user-attachments/assets/bac53c59-e0f8-4d04-a255-5f063779e35d" />



After that, you will then be prompted "How are you planning to use this fork?", as seen in the image below. Select the "To contribute to the parent project" option and continue.
<img width="953" height="655" alt="image" src="https://github.com/user-attachments/assets/01a73c07-7720-4ffe-89d9-3d4db0c91a67" />



You will now notice that the symbol on the left of your "Current repository" has changed. You are now editing your own copy (your fork) of the Community Server repository. By pressing the "Commit file to main" button below you will send the changes you've made to your fork. Then, by pressing the "Push Origin" button, you will apply those changes. Things should somewhat resemble the image below.
<img width="961" height="659" alt="image" src="https://github.com/user-attachments/assets/5f18df24-fc67-490f-ade3-cd289646609c" />






Now that you have applied (Push Origin) your changes (Commit) to your copy of the main repository (Fork), you need to create a Pull Request so that i may review your changes and adopt them to the Community Server main repository. This can be done through your Forks' GitHub page, as seen in the image below. (you can press the "View on GitHub" button to be directed directly to the repository, from there simply find your fork among whichever others there are.
<img width="948" height="376" alt="image" src="https://github.com/user-attachments/assets/b5903d44-d5a9-47e7-91fc-9ab18c4feed8" />



By clicking "Create Pull-Request" or "Open Pull-Request" you will be directed to another GitHub page. This is where you will name and describe your changes directly to me so that I may review them later and "merge" your changes to the main Community Server repository.
<img width="1262" height="884" alt="image" src="https://github.com/user-attachments/assets/9bbfb1b8-9883-4d7c-8ef5-630dd40e1013" />




When I acess the GitHub page of the Community Server, it will have an open Pull Request. It will look as such when i go to review it (image below).
<img width="2174" height="1289" alt="image" src="https://github.com/user-attachments/assets/aa933d9a-404d-49d6-8a2c-cf7d3e59d0c3" />



Once I merge the Pull Request, it is officially integrated into the main repository, as seen below. I will then take the now updated main repository and personally update the Server files onto Virtual Machine that HB is allowing us to host from. I can't quite promise a especific frequency as to how often I will do that, but it for the sake of having one, i'll guarantee a half-daily check up (every 1 or 2 days).
<img width="1426" height="418" alt="image" src="https://github.com/user-attachments/assets/e8242c68-f100-46e4-baaa-9477a2a4e834" />


Also, considering the possibility of multiple pull requests at the same time, we may have several merging conflicts. If this does ever happen, I will delete all conflicting Pull Requests and personally make all changes to the Server files according to each of the commit changes, in order by which pull request was published first to last.


That's all really. Any and all communication in regards to server files are to be done externally, aka. most likely one of the ED discords. If anything major happens in terms of upkeep or moderation of these server files, please do contact me (markus_adude on discord) (I'll probably know about it, but user feedback always gives better insight into the problem).


