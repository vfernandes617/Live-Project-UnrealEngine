# Unreal Engine Live Project
During my time at the Tech Academy I working on a live project to build a game in the Unreal Engine. This was a two week sprint and the code was consisted entirely of Unreal Engines Blue print scripts.
This was an apprenticship done for [Prosper IT Consulting](https://www.linkedin.com/company/prosper-it-consulting/) we participated in daily stand-ups with a small team. The goal was to deliver a minimal viable product by the end. For this MVP I was tasked with creating a sandbox game. I went with a version  of American Ninja Warrior. There were quiet a few mechanics and phyics  that I can to create in order to fully realize this game.

Below are some examples code and logic I have for this project.
## Index

- [Main Menu](#MainMenu)
- [Sprint Logic](#Sprint)
- [Respawn](#Respawn)
- [Timer](#Timer)
- [CheckPoint](#Checkpoint)
- [Ragdoll effect](#Ragdoll)
- [Proficiencies](#Proficiencies)
## MainMenu
  For my Main menu I create an empty level and created a user widget and titled it WB_Title. I first started off by dragging in a Canvas panel where I would later create my buttons to play or quit the game if the player wants.
I kept the title screen basic and focused prodomentily on making her the play and quit buttons work. When the player hit the play button it will load the main game scene title Level01.
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/Images/Widget%20logic.png)
For the both the play and quit button I made both button variables I can reference in my event graph. To get the play button to work I connected the node to an object by reference and have it call my Level101.
For the quit button I simply used the node "Quit" to end the game once pressed.

## Sprint Logic
For my sprint Logic I created an enhanced InputAction button using the SHIFT key to trigger. The players walk speed than goes from 500 to 1000 while the player holds SHIFT. When player chooses to let go of the SHIFT key the action is completed reverting players movement back to 500. For the target I created a variable called "Character movement" references the player character.

