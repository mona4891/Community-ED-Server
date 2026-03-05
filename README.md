Heyo it's A Dude/Markus, this ReadMe aims to explain and tutorialize how to edit the Community Server files here in this repository.
I've sectioned things in the followng chapters:

1. How Server Files Work
2. Managing GameMode Rotation (Mods included)
3. Using GitHub Desktop Desktop

‎ 
‎ 


#  **1. How Server Files Work:**

There are three main folders pertaining to the gamemode rotation in a server:
"server", "map_variants" and "game_variants"
<img width="1173" height="329" alt="image" src="https://github.com/user-attachments/assets/a011ef6f-3686-4e88-ad54-841020fa6aa6" />

‎ 

"server" contains text files that actively control the rotation. These files must be open with a text editing software, it is highly reccomended to download either notepad++ or VSC (Visual Studio Code).
<img width="1173" height="276" alt="image" src="https://github.com/user-attachments/assets/6d32bea2-3a34-4ffc-a726-7b95b9a8b082" />

‎ 

"map_variants" and "game_variants" contain, respectively, all map and variant files which are housed in their own folders adequately named to each map/variant.
In each folder from individual maps/variants there will be ED especific files, such as "sandbox.map" or "variant.koth". Make sure to not mix these files up in different folders.
<img width="1160" height="280" alt="image" src="https://github.com/user-attachments/assets/8bbd435c-3bda-412b-94e7-eeef05e493ba" />
<img width="1158" height="795" alt="image" src="https://github.com/user-attachments/assets/9445685c-55de-421e-a469-efb699a03390" />


‎ 
‎ 

#  **2. Managing GameMode Rotation (Mods included):**

The GameMode Rotation in a server is mainly controlled by the "voting.json" file. Aside from the initial set of Core Maps (Valhalla, Standoff, etc...), each GameMode is inserted into rotation in the following format:

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

The download links as seen in the example above were given by ED discord moderators and modders. Unless available from another source (currently you can use Buckarooo's Fileshare site), I reccomend consulting those people if you're looking for download links to any mods.


(FFS I'm stil structuring this damn thing, stop reading this shits a WIP, gtfo lil bro)

