# Unity3D Training

The game engine we've chosen for this project thankfully has a [comprehensive documentation](https://docs.unity3d.com/Manual/index.html) site that includes both a [general purpose manual](https://docs.unity3d.com/Manual/index.html) and a [scripting api](https://docs.unity3d.com/ScriptReference/index.html).

For more information please visit the official Unity Documentation!

## Crash Course

Anything that has a spatial existance in the game engine is a GameObject, which can be toggled on and off and given a unique name. GameObjects automatically attach and are required to have a Transform Component that stores spatial data such as position, rotation, and scale. The Transform component is primarily used for 3D, but there is also a RectTransform variant with settings built for 2D games and UI systems.

Unity uses a Component-based system for it's core game features. What this means is that you aren't going to be defining your features on the entities directly like object oriented systems; you'll be defining your features in terms of plugin-like script that gets attached to generic objects.

You can still create your usual C# object oriented classes and define your own APIs. It's just the game content itself is built using a Component architecture.


### The MonoBehavior Class
The MonoBehavior class is the Unity provided C# class that all your components will derive from. In fact when you create a script in-editor Unity will automatically create an templace C# script deriving from MonoBehavior and including some starter functions. This class provides access to a lot of engine features and provides a large host of Overridable Functions (see below) that are automatically called by the game engine at specific intervals and for specific reasons.


### Overridable Functions
This is not all of the overridable functions! This is just a quick list for reference!
#### Awake()
Awake is called when the script is loaded on the object it's attached too. Notably other scripts or objects nearby may not be loaded yet! So it's best to only use this for internal setup. This only gets called once!

#### Start()
Start is called on the very first frame the game object is active and typically gaurunteed to be called **after** `Awake()` has been run. Note that this may not be run again if the game object is toggled use `OnEnable()` for things that need to be run every time the object is toggled on.

#### Update()
`Update()` is called every single frame. You can use `Time.deltatime` to get a float number that equals the number of simulation seconds since the last time update was called. You should generally only use this for calculations or physics that **need** to be run every frame, like player movement or vehicle control physics, anything framerate or camera dependent.

Don't forget to scale any movement by `Time.deltatime` so that your movement code does not become arbitrarily framerate dependent. `Time.deltatime` will always scale proportionally with framerate, that way someone with twice the FPS as someone else doesn't unintentionally move twice as fast.

#### FixedUpdate()
`FixedUpdate()` runs on the game engine's physics tick. It's expensive to always be calculating physics every frame, so it delegates the physics crunching to a separate update cycle which runs at a more standardized number of times a second, reguardless of framerate.

Just like `Update()`, you can use a similar value `Time.fixedDeltatime` to get the number of simulation seconds since the last `FixedUpdate()` was called in order to scale movement code accordingly. 

You should generally try to put any calculations or checks that need to run *a lot* here first to avoid running them an unnessecary number of times for every frame and driving down the framerate. If it's not framerate dependent; it should probably be here instead of `Update()`;

#### OnGUI()
Similar to `Update()`, it runs on every frame. We will likely be using the UICanvas system for our UI so this may only be usefull for creating debug UI and visualizations, but still a good function to know about.

#### OnEnable()
Self explanatory, called every time the object gets enabled. 

#### OnDisable()
Also self explanatory, called every time the object gets disabled.

#### OnDestroy()
Called once and only once when the object this script is attached to gets a call to be deleted or the scene it's in unloads. Usefull if you need to perform destructor like cleanup.

### Component Flags
#### Require Component
If you know your script **needs** access to a particular other component on the same gameobject, you can have the engine force this object to have that type of component by placing `[RequireComponent(typeof(MyComponentClassname))]` before your class declaration in your component's script. Whenever attatching your script, or if your script is saved in a prefab, the engine will automatically attach that script to the gameobject as well as prevent it's removal. Be careful with this however; **it is not automatically reverssible**.

#### Don't Destroy On Load
This is a weird flag that can only applied at runtime using `DontDestroyOnLoad(referenceToObject);`. What this does is prevent `Destroy()` from being automatically called on the object during scene changes, that's it! It's extremely usefull for singleton gameobjects or centralized managers that need to be tangible but should never be destroyed by scene changes. 

Importantly, but also obvious, you'll need to remember to manually call `Destroy()` on the object when you later *do* want to destroy it, especially on a scene change.


### Scene Loading
Scene loading has an interesting architecture in Unity. Scenes must be predefined, and **must** be added to the build instructions in order to be loadable, period. You can add your scene to the build order by going to `File > Build Settings...`. Note that the first scene listed here will be the one that is automatically loaded first, so take consideration on where you put it in the list!

In any script you can load a scene using the `SceneManager.LoadScene("SceneName");` function.