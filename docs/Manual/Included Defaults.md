# Included Defaults
To make things faster and easier, we've included some premade default utility scenes, scripts, and prefabs. You aren't required to use them, by any means, but they do accelerate early development and provide nice examples for beginners.


## Splash Screen
Unity has a strange quirk where the first scene loaded after starting the game has many rendering functions reduced. The idea is that you use this scene exclusively to display your company logo or any other splash screens you need, but in practice even these can look bad.

So to remedy this, we've included a simple blank black splash screen that automatically loads whatever you want your "first" proper scene to be. To use it, make sure that the `Splash` scene is first in your game's scene export order. Next, open up the `Splash` scene and click select the `SplashController`.

Now in the Inspector tab, you should see a component you can control the values of. 

![alt text](../img/SplashControllerExample.png)

**Delay:** The number of seconds the splash screen will wait. You can set this to 0 to make it as instant as unity can handle.
**Next Scene:** The _exact_ *case sensitive* name of the scene you want the splash screen to change too when it's done.


## Main Menu
A simple Main Menu made from Unity canvas components, includes a `MainMenuHelper` class that exposes arbitrary scene loading and game quitting functions to the unity Event System that canvas clicks can trigger.

**Note:** Qutting the game functions do not work in the editor! (This is a quirk of Unity, there is a warning about it when a quit is requested.)

## DemoScene
We've included our own prototye environment that we used to test our own features.