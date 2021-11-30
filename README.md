# OldVR-Coursework
Old VR project from uni I would like to preserve


## Student Number: 27014939
## Module: VR
## Overview of The World

For this project I decided to create a VR world with a Medieval Fantasy theme to it. The world is set 
in a forest like environment which grass textures, meadow hills and large trees. The user begins 
inside of a medieval home and can then venture out and explore the world.

The worlds main attractions are the three dragons which it contains. Each dragon is contained within 
a castle and each of them have their own unique personality and animations. The dragons are all 
very disruptive, and so you have been tasked with blowing them all up.
The user has a list of tasks they can perform in the world in the top left. The item number 
corresponds to the keyboard control the user must input (e.g Task 2 can be completed by pressing 
“2” on the keyboard).

The user can interact with the world through a series of interactable objects. The basis of the game 
was originally constructed for use in VR only. Hence the user can traverse the environment using any 
popular VR headset and controllers.

As some people suffer from severe motion sickness, I chose to build most of the interactable 
portions of the game with keyboard controls in mind. Despite this you can still pick up and throw 
objects such as bombs and weapons with VR controllers. Hand animations have also been included 
when using VR controllers, which create a sense of realism you can’t get with the keyboard.

## IMAGE

Each of the three castles and dragons inside of the world react differently to the explosions the user 
can set off. The first castle’s dragon leaves behind smoke, the second gets blown into space, and the 
third leaves behind flames.

## Controls

In VR the scene can be traversed through using a teleportation system. You’ll notice whether you are 
in VR or not, a raycaster shooting out of the right arm of the player object. When this raycaster is 
red, the area that is being pointed at cannot be teleported to. When it is white it can be.

## IMAGE

The entire scene in VR only has one action button, which is the rear trigger on both controllers. If 
your VR controllers has a side trigger or a secondary back trigger, it’s possible this will be the action 
button and you should test them out.

The action button can be used to teleport (when pressed on the right hand controller), and it can 
also be used to grab objects and interact with them (weapons for example).

Outside of VR, the user can traverse the environment using the WASD keys. Pointing your mouse 
cursor in a specific direction will cause the player to travel in that direction also. So it is possible that 
you can hold down the W key and turn right, left etc. All interactions which are triggered via a 
keyboard are listed in the top right. The user can see 6 items which they can perform in the world, 
using keys 1-6.

The three dragons which the user can kill are present outside of the house, and the house fire can be 
seen both inside and outside of the house on the right side of the roof.

## Scripts

### VR Control Scripts

Most of the scripts attached to the “VR Rig” object allow for the user to traverse the environment in 
VR and interact with objects using VR controllers.

Some such as “XR Rig”, “Teleportation Provider” and “Locomotion System” are built in scripts which 
come with Unity’s XR package that were simply added to the appropriate game objects.

The “Hand Presence” script was custom written and is attached to the right and left “Hand 
Presence” objects (child objects of “Right Hand” and “Left Hand”) in order to locate the VR 
controllers, add them as a game object and allow us to attach models and animations to them. You 
will get an error in the console if VR controllers are not connected, but this does not prevent you 
from playing with mouse and keyboard.

The input to the action button on the VR controllers is saved as a floating-point number to a variable 
in order to define how open or closed the users virtual hands should be. This allows for realistic hand 
animations when grabbing objects and interacting with them. 

### Keyboard Control Scripts

The “Keyboard” script attached to the VR Rig is used to allow the user to manoeuvre the 
environment via a keyboard and mouse. The WASD keys are triggered using if loops, and the 
transform.position property is then updated at a constant speed to reflect this.

In addition to this a second script for player movement via keyboard and mouse called “Camera 
Thing” is attached to the VR camera. This scripts job is to turn the players body to face the position 
of the cursor. This way when a user turns around and presses W, they move forward not back 
backward.

### Opening/Closing Front Door Script

The front door of the house is controlled used the “keyAnimator” script, which switch a Boolean 
variable to either true or false based on use input. The default state is false, which means the door is 
shut, however if you press “1” on the keyboard this sets it to true which then triggers the door 
opening animation.

### Explosion/Killing Dragon Scripts

The user can kill each of the three dragons by detonating a selection of bombs which have been 
conveniently placed inside of each castle.

These explosions and subsequent killing of the dragons take place in scripts “Explosion”, 
“Explosion2” and “Explosion3” (one for each castle).

As mentioned in the overview section, each explosion is slightly different to each other.
The firs Explosion script simply plays a particle effect using Unity’s own free particle pack (see assets 
section) at the position of the bombs, and then destroys the dragon model. In it’s place a smoke 
particle effect which is set to occur on loop is instantiated. Explosion3 works in basically the same 
way.

The second script “Explosion2” is very similar to the first, except inside of the Explosion() function, 
there is some additional code which is used attach some for to every rigid body component within a 
specific radius.

### House Fire Script

The house fire script is used to set out the house fire when the user presses the “6” key. This sets off 
a water animation on the roof of the home, and destroys the flame animation which is already 
playing.

The flame animation is on loop but has been set to stop when the “Destroy()” function is called. 

Hence in this script when the user pressed the button “6” (using an if loop) the destroy function is 
called on the fire GameObject. At the same time a new GameObject is instantiated using the 
Instantiate() function at the same coordinates.

This new game object is the water particle animation, which continues for 10 seconds

## Third Party Assets Used

Mega Fantasy Props Pack (Used for home mainly) - https://assetstore.unity.com/packages/3d/environments/fantasy/mega-fantasy-props-pack-87811

Medieval Castle Pack Lite (Used for castles) - https://assetstore.unity.com/packages/3d/environments/dungeons/medieval-castle-pack-lite-51230

Four Evil Dragons HP - https://assetstore.unity.com/packages/3d/characters/creatures/four-evildragons-pack-hp-79398

Breakable Windows (House windows) - https://assetstore.unity.com/packages/tools/particleseffects/breakable-windows-110383

Unity Particle Pack (Explosions and Water) - https://assetstore.unity.com/packages/essentials/tutorial-projects/unity-particle-pack-127325

VR Hands – Via Oculus Files

## Reflections

Upon reflection I feel that the VR world is along the lines of what I wanted it to be, however there is 
still room for improvement. When killing the dragons, a death animation could be triggered to give 
the user more realism. In addition to this, instead of having the dragons run the same animation 
loop regardless of the situation, they could instead react to player movement. Perhaps become 
more threatening the closer the player is to them.

I think there could also be some more interaction when using the VR. Perhaps the user could battle 
the dragons with the weapons outside. This could also lead to a HP system, which would introduce 
life and death in the game.

There is a lot of areas where some of my basic concepts could be developed much further. However, 
I feel my current demo lays a solid foundation for this, and provides a fun and interesting look into 
VR development and what’s possible with Unity








