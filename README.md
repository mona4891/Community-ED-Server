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


> This repository (this folder of files) is made public so that anyone may see it. You will clone this repository locally to your computer and edit those local files. By editing these files you will create a "fork" of the Community Server repository (your own version of the "main" repository). You can submit your changes to the "main" repository by creating a pull request, which will be reviewd by me (to check for errors/bitcoin miners) before accepted and merged into the main repository, which will make your changes official.


> How these changes will be done is mainly through the GitHub Desktop app.
> 1. You will log in to your GitHub account
> 2. You will clone/download the repository files (URL: https://github.com/A-Dude101/Community-ED-Server), allowing you to change them as you see fit
> 3. Pull from origin (refresh your files so that they match the "main" repository)
> 4. The app will automatically recognize all these changes you make, grouping them up in a "commit" to you "fork"
> 5. Due to not being a main author of the main repo, it will also prompt you to create a pull request for me to review and then merge your "fork" to the main repository.
>
>    All in all, GitHub desktop just makes things easier for you to make these changes, I highly encourage using it.

‎ 
‎ 


As a first, make sure to create a GitHub account and download GitHub Desktop, linking it to your account. The application will look something like the image below:
<img width="1649" height="1020" alt="image" src="https://github.com/user-attachments/assets/07c24368-0470-41fc-b221-da72281a1210" />


After loging in and having linked the account in the GitHub Desktop app you will need to download this repository to you local PC storage. Clicking on the "File" tab up top, then on "Clone Repository..." you must only fill in the Repository URL with the following link: https://github.com/A-Dude101/Community-ED-Server
Once that is done, choose a folder in your local PC to house these repository files (it must be an empty folder)

<img width="745" height="436" alt="image" src="https://github.com/user-attachments/assets/1073cc4b-9b5e-4076-b221-63b6c5f789db" />




At this point, the editing process is fully functional. All changes you make will be grouped up in an action called "commit". You will be prompted to "commit" to main, but will not be able to considering you are not the author of the Community Server repository. For this you will be prompted to make your own "fork" (copy) of that repository, as seen below
<img width="824" height="508" alt="Captura de tela 2026-04-08 092128" src="https://github.com/user-attachments/assets/60100af2-9208-4dca-bba6-2c76cdefce8d" />



Having made your commit onto your own fork of the Community Server repository, you will be prompted to "Push Origin", this simply means to make your commit changes official in your own fork. It'll look as it does below, simply press push origin to confirm your commit.
<img width="1638" height="1001" alt="image" src="https://github.com/user-attachments/assets/0462afff-4f0b-48c6-80b2-34735637d170" />



Now that you have your fork with the changes you wish to see, you need to create a pull request so that i may review your changes and adopt them to the actual Community Server main repository. You will change your current "main" branch (as demonstrated on the image below) to the "Pull-Request-Branch". This will prompt you to create a Pull Request.
<img width="1631" height="1008" alt="image" src="https://github.com/user-attachments/assets/47c20d71-0ac3-4dc6-b8d2-9b963aacafa4" />


By clicking "Create Pull-Request" you will be directed to an internet browser GitHub page. This is where you will name and describe your changes directly to me so that I may review them later and "merge" your changes to the main Community Server repository.
<img width="1983" height="1354" alt="image" src="https://github.com/user-attachments/assets/653f13cb-1777-49d2-8ec8-e085a0eec250" />



When I acess the GitHub page of the Community Server, it will have an open Pull Request. It will look as such when i go to review it (image below), except for that revert action, purely to keep the repo as it was before making this tutorial.
<img width="1402" height="1047" alt="image" src="https://github.com/user-attachments/assets/69d2815c-2b44-4927-bfd9-6617948a1a7f" />


Once I merge the Pull Request, it is officially integrated into the main repository, as seen below. I will then take the now updated main repository and personally update the Server files onto Virtual Machine that HB is allowing us to host from. I can't quite promise a especific frequency as to how often I will do that, but it for the sake of having one, i'll guarantee a half-daily check up (every 1 or 2 days).
<img width="1426" height="418" alt="image" src="https://github.com/user-attachments/assets/e8242c68-f100-46e4-baaa-9477a2a4e834" />


Also, considering the possibility of multiple pull requests at the same time, we may have several merging conflicts. If this does ever happen, I will delete all conflicting Pull Requests and personally make all changes to the Server files according to each of the commit changes, in order by which pull request was published first to last.


1. Open GitHub Desktop
2. Pull/Fetch Origin (To refresh local files)
3. Make changes
4. Appropriately name and write the description of the changes in your commit
5. Open Pull Request for me to Review

That's all really. Any and all communication in regards to server files are to be done externally, aka. most likely one of the ED discords. If anything major happens in terms of upkeep or moderation of these server files, please do contact me (markus_adude on discord) (I'll probably know about it, but user feedback always gives better insight into the problem).


