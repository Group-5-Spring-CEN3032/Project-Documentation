# Player Movement
Our `PlayerMovementController` is a simple First-Person player controller similar to many games of the genre. The controller uses the [Unity Input API](https://docs.unity3d.com/ScriptReference/Input.html) to make configuring it's signals for different devices easier.

The movement Controller also correctly responds to the [Pausing API](./Pausing%20API.md)! Any inputs given while the game is paused will be completely ignored, you must explicitly make the call to unpause the game from your pause menu.

## Modifyable Variables
These variables are open to your configuration to customize your controller for your game.

**Camera Axis:** A reference to the camera, or parent of the camera that should be directly rotated for vertical view rotation. The entire player object is rotated for horizontal view rotation.
**Mouse Sensitivity:** A flat multiplier for the X and Y movement of the mouse respectively.
**DegreesPerSecondLookSpeed:** The number of degrees per second the player's view is allowed to rotate.
**Max Angle:** The furthest upward the player is able to look along the Y-Axis.
**Min Angle:** The furthest downward the player is able to look along the Y-Axis.
**Movement Mult:** A flat multiplier of player movement.
**Jump Force:** A flat multiplier of the instantaneous physics force applied to perform a jump. You can think of this of the *amount* of force one pushes off the ground to perform a jump.
**Time Between Jumps:** The time in seconds that must elapse between two jumps.
**Ground Detection Distance:** The approximate distance from the bottom of the player a ground collider must be in order for a player to be considered "on the ground".