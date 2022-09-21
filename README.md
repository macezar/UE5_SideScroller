# UE5_SideScroller
A simple side scroller experience based on Lyra framework released by Epic Games.


### Movement:
Two approaches to movement.
- Remove the input from the input mapping, that way you can only input left or right when moving the pawn.
- Add a new variable to control if the movement is permited on Y plane.

I went with the second option, as to allow the inputs when needed, and because I plan to use volumes to change how the camera works during certain parts of the game. A good example of this would be Nier, where you have the normal 3d movement which changes to 2.5D when walking into certain areas of the map.

### Facing direction:
Added a new variable that can be accessed by blueprint that allows the pawn to turn towards the movement instead of always facing the same direction than the camera.

### Abilities:
Another issue I faced when dealing with the ability system is that the game uses the camera instead of the pawn to calculate the direction. Works fine if you are playing a 3d fps game which the character is always facing the same direction of the camera. Not so much when you are not.

For those changes, in each GA_Ability_File, check the direction segment and replace the reference from the camera to the actor.
![image](https://user-images.githubusercontent.com/5649304/191574061-398642eb-fd71-482c-9418-b0ba852f2468.png)

### Weapon Fire:
There's a pre-define enum in the code that changes how the firing works. I've changed from CameraTowardFocus to WeaponForward. That makes weapon fires to the same direction the character is facing.
