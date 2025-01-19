# Unreal Engine Live Project
During my time at the Tech Academy I working on a live project to build a game in the Unreal Engine. This was a two week sprint and the code was consisted entirely of Unreal Engines Blue print scripts.
This was an apprenticship done for [Prosper IT Consulting](https://www.linkedin.com/company/prosper-it-consulting/) we participated in daily stand-ups with a small team. The goal was to deliver a minimal viable product by the end. For this MVP I was tasked with creating a sandbox game. I went with a version  of American Ninja Warrior there were quiet a few mechanics and phyics that I can to create in order to fully realize this game.

Below are some examples code and logic I have for this project.
 Index

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
  
---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/Images/Widget%20logic.png)
---
For the both the play and quit button I made both button variables I can reference in my event graph. To get the play button to work I connected the node to an object by reference and have it call my Level101.
For the quit button I simply used the node "Quit" to end the game once pressed.

## Sprint Logic

For my sprint Logic I created an enhanced InputAction button using the SHIFT key to trigger. The players walk speed than goes from 500 to 1000 while the player holds SHIFT. When player chooses to let go of the SHIFT key the action is completed reverting players movement back to 500. For the target I created a variable called "Character movement" references the player character.

---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/Images/Sprint.png)
---

## Respawn
I set my blueprint in the following order.
1. Custom Event: Respawn
Purpose: This is a custom event named Respawn. It acts as the entry point for this logic, triggered when something (like the player or a component) needs to respawn or reset.
2. Set Node: Ragdoll?
Purpose: This  toggles a variable called Ragdoll? (a Boolean).
Effect: The Boolean controls whether the character or object is in a ragdoll state, which usually means physics simulation is enabled. Setting this variable here might signal the system to stop ragdolling during the respawn process.
3. Attach Component to Component
Purpose: This node reattaches a component (e.g., a character's skeletal mesh or a detached part) to a parent component.
Parameters:
Target: The component being reattached (likely set to a skeletal mesh or physical object).
Parent: Specifies the component to which it will attach. In this case, it's attaching to the pelvis socket of the parent (likely part of a skeleton or mesh).
Location/Rotation Rules: Set to Keep Relative, meaning the component retains its relative position and orientation when reattached.
Weld Simulated Bodies: Checked, so the physics bodies of the two components will merge for realistic behavior.
4. Set Relative Location and Rotation
Purpose: Adjusts the position and rotation of the reattached component relative to its parent.
Details:
New Location: (0, 0, -89.0), meaning it positions the component slightly below its parent.
New Rotation: (0, 0, 270.0), setting its orientation.
Teleport: Checked, ensuring instant repositioning without interpolation.
5. Set Actor Transform
Purpose: Adjusts the position, rotation, and scale of the entire actor (likely the player or object being respawned).
Details:
New Transform: A specific transform (position, rotation, scale) passed in via a pin. This places the actor at the designated respawn location.
---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/Images/Respawn.png)
---
## Timer

To Track the players time during their track through the game I used a Widget and called it Timer_WB. The blueprint starts off with  an Event Construct node which triggers as soon as the player starts the game. It connects to the "Set Timer by Event" node this node is set to call the "IncreaseTime custom event node every 1 second. With the looping box checked it ensures the timer repeats indefinitely. The event is executed every second by the timer the logic increments a time variable "Sec" and handles updating the display.
The Sec variable is incremented by 1 each time teh IncreaseTime even is called. Once the seconds reached 60 it will branch and start back at zero and increment the variable minute by 1.

---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/Images/Timer.png)
---

 ## Checkpoint
---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/GIFs/Checkpoint.gif)
---

The checkpoint was created to have a save point so the player can respawn closer to the end goal. To trigger the checkpoint I created an on component begin overlap that activates whenever the thirdperson character gets close to the flag than used a Get World Transform to pin point the exact location of the player character and respawn it at that location.

## Ragdoll
---
![Project Screenshot](https://github.com/vfernandes617/Live-Project-UnrealEngine/blob/main/GIFs/RAgdoll.gif)
---

The Ragdoll effect was created so whenever the player character hit on obstacle they will go into a ragdoll and respawn. This is so the player character knows that they hit an object they shouldnt have and to avoid hitting. 

