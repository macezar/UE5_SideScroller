# UE5_SideScroller
A simple side scroller experience based on Lyra framework released by Epic Games.


### Movement:
Two approaches to movement.
- Remove the input from the input mapping, that way you can only input left or right when moving the pawn.
- Add a new variable to control if the movement is permited on Y plane.

I went with the second option, as to allow the inputs when needed, and because I plan to use volumes to change how the camera works during certain parts of the game. A good example of this would be Nier, where you have the normal 3d movement which changes to 2.5D when walking into certain areas of the map.

### Facing direction:
Go to B_Hero_ShooterMannequin, and change some Character Movement settings. Enable Orient Rotation To Movement in the Character Movement Component and disable Use Controller Rotation Yaw in the Character Defaults.

### Abilities:
Another issue I faced when dealing with the ability system is that the game uses the camera instead of the pawn to calculate the direction. Works fine if you are playing a 3d fps game which the character is always facing the same direction of the camera. Not so much when you are not.

For those changes, in each GA_Ability_File, check the direction segment and replace the reference from the camera to the actor.
![image](https://user-images.githubusercontent.com/5649304/191574061-398642eb-fd71-482c-9418-b0ba852f2468.png)

### Weapon Fire:
There's a pre-define enum in the code that changes how the firing works. I've changed from CameraTowardFocus to WeaponForward. That makes weapon fires to the same direction the character is facing. A further moditication would be change weapontowardfocus, and change the game to make the animation target follow the mouse movement, that way wou can shoot where the mouse is, but still in the same plane as the pawn.


### Camera:
Instead of creating a new camera mode. I've made mofidications to the existing CM_ThirdPerson camera. In the ThirdPersonOffsetCurve, change the lines to match your the desired curve. Currently I'm using:
![image](https://user-images.githubusercontent.com/5649304/191715327-d993c274-a4c8-4a05-a0c0-0e36691333c3.png)

And the result is:
![image](https://user-images.githubusercontent.com/5649304/191715506-e08936fb-1c47-49b0-84fc-8576094dbd4a.png)



