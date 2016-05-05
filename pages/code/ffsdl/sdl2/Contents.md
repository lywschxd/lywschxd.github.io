#  Beginning Game Programming v2.0

>这个文档摘抄至[Lazy Foo' Productions](http://lazyfoo.net/tutorials/SDL/index.php#Hello), 这里进行记录，方便阅读查看

Greetings everyone, welcome the ground up recoding of Beginning Game Programming with SDL. This time we will be coding with SDL 2 which has been released on the [SDL website](http://www.libsdl.org/).

These tutorials were designed for C++ programmers who want to move from text based games to real time games with graphics. By the end of these tutorials, you'll know the basics to make your first real video game!

|  lesson |name|desc|
|---------|:---:|---:|
|Lesson 01|[Hello SDL](Hello_SDL.md)|In this tutorial we will be setting up the SDL library and creating our first window.|
|Lesson 02|[Getting an Image on the Screen](Getting_an_Image_on_the_Screen.md)|ow that we can get a window to appear, lets blit an image onto it. |
|Lesson 03|[Event Driven Programming](Event_Driven_Programming.md) |Here we'll start handling user input by allow the user to X out the window.|
|Lesson 04|[Key Presses](keypress.md)|Here we'll learn to handle keyboard input.|
|Lesson 05|[Optimized Surface Loading and Soft Stretching](Optimized_Surface_Loading_and_Soft_Stretching.md)|Now that we know how to load and blit surfaces, it's time to make our blits faster. We'll also take a smaller image and stretch it to fit the screen.|
|Lesson 06|[Extension Libraries and Loading Other Image Formats](Extension_Libraries_and_Loading_Other_Image_Formats.md)|Here we'll be using the SDL_image extension library to load png images.|
|Lesson 07|[Texture Loading and Rendering](Texture_Loading_and_Rendering.md)|A big new feature in SDL 2.0 is hardware accelerated texture based 2D rendering. Here we'll be loading an image to render it using textures.|
|Lesson 08|[Geometry Rendering](Geometry_Rendering.md)|Another new feature in SDL 2.0 is hardware accelerated primitive rendering. Here we'll be using it to render some common shapes.|
|Lesson 09|[The Viewport](The_Viewport.md)|SDL 2.0 also lets you control where you render on the screen you using the viewport. We'll be using the viewport to create subscreens.|
|Lesson 10|[Color Keying](Color_Keying.md)|Here we'll use color keying to give texture transparent backgrounds.|
|Lesson 11|[Clip Rendering and Sprite Sheets](Clip_Rendering_and_Sprite_Sheets.md) |Using clip rendering, you can keep multiple images on one texture and render the part you need. We'll be using this to render individual sprites from a sprite sheet.|
|Lesson 12|[Color Modulation](Color_Modulation.md) | We'll be altering the color of rendered textures using color modulation. |
|Lesson 13|[Alpha Blending](Alpha_Blending.md) |Here we'll be using SDL 2.0 new hardware accelerated alpha blending. |
|Lesson 14|[Animated Sprites and Vsync](Animated_Sprites_and_Vsync.md) |Here we'll be using a sequence of sprites to animate them. |
|Lesson 15|[Rotation and Flipping](Rotation_and_Flipping.md) |Here we'll be using SDL 2.0's new texture rotation and flipping. |
|Lesson 16|[True Type Fonts](True_Type_Fonts.md) | Here we'll be rendering text from true type fonts using SDL_ttf.|
|Lesson 17|[Mouse Events](Mouse_Events.md) |Here we'll learn to read mouse input using mouse events. |
|Lesson 18|[Key States](Key_States.md)| There's other ways to read the keys besides event polling. Here will get the current states of the keyboard using get states.|
|Lesson 19|[Gamepads and Joysticks](Gamepads_and_Joysticks.md)|Here we'll learn to read input from a game controller. |
|Lesson 20|[Force Feedback](Force_Feedback.md)|Another new feature for SDL 2.0 is rumble support using the SDL haptics. We'll make our controller rumble when a button is pressed.|
|Lesson 21|[Sound Effects and Music](Sound_Effects_and_Music.md)|Here we'll be using SDL_mixer to add music and sound to our SDL App.|
|Lesson 22|[Timing](Timing.md)|Here we'll be using SDL's time capabilites.|
|Lesson 23|[Advanced Timers](Advanced_Timers.md)|Here we'll extend SDL time capabilities to make our own custom timer.|
|Lesson 24|[Calculating Frame Rate](Calculating_Frame_Rate.md)|Here we'll use the timers we built to measure frame rate.|
|Lesson 25|[Capping Frame Rate](Capping_Frame_Rate.md)|If you need a constant frame rate when vsync isn't available, frame rate capping can be used as a fall back.|
|Lesson 26|[Motion](Motion.md)|Here we'll be taking what we learned about render and handling input to make a dot move around the screen.|
|Lesson 27|[Collision Detection](Collision_Detection.md)|Here we'll have two objects interact with each other using bounding box collision detection.|
|Lesson 28|[Per-pixel Collision Detection](Per-pixel_Collision_Detection.md)|Here we'll have two object collide using per-pixel collision detection.|
|Lesson 29|[Circular Collision Detection](Circular_Collision_Detection.md)|Here we'll learn to detect collisions with circles and boxes.|
|Lesson 30|[Scrolling](Scrolling.md)|Here we'll be implement a camera to scroll levels larger than the screen.|
|Lesson 31|[Scrolling Backgrounds](Scrolling_Backgrounds.md)|Here we'll using a scrolling background to give the illusion of an infinite level.|
|Lesson 32|[Text Input and Clipboard Handling](Text_Input_and_Clipboard_Handling.md)|Here we'll using SDL 2.0's new way of handling text input and its new clip board handling feature.|
|Lesson 33|[File Reading and Writing](File_Reading_and_Writing.md)|Here we'll using SDL's RWOps API to do binary file IO.|
|Lesson 34|Audio Recording|SDL 2 is planned to have an audio recording feature. As of SDL 2.0.0, it is not yet implemented. This here is just a place holder until it is ready to go.Please do not e-mail me saying this link is broken. You'll just look silly.|
|Lesson 35|[Window Events](Window_Events.md)|Here we'll be handling events from a resizable window.|
|Lesson 36|[Multiple Windows](Multiple_Windows.md)|A new feature in SDL is the ability to support more than one window. Here we'll make an application that has 3 windows.|
|Lesson 37|[Multiple Displays](Multiple_Displays.md)|Another new feature of SDL 2.0 is the ability to handle more than one physical display. Here we'll make our window jump from display to display.|
|Lesson 38|[Particle Engines](Particle_Engines.md)|Here we'll use a simple particle effect to create a simple trail effect.|
|Lesson 39|[Tiling](Tiling.md)|Here we'll make a simple level using a tiling engine.|
|Lesson 40|[Texture Manipulation](Texture_Manipulation.md)|Here we'll be directly accessing and manipulating a texture's pixels.|
|Lesson 41|[Bitmap Fonts](Bitmap_Fonts.md)|Here we'll be using a texture as a font using bitmap font techniques.|
|Lesson 42|[Texture Streaming](Texture_Streaming.md)|Here we'll be rendering from a streaming data source using texture streaming.|
|Lesson 43|[Render to Texture](Render_to_Texture.md)|Here we'll be taking a scene and rendering it to a texture.|
|Lesson 44|[Frame Independent Movement](Frame_Independent_Movement.md)|Here we'll be making the dot move independent of the current frame rate. |
|Lesson 45|[Timer Callbacks](Timer_Callbacks.md)|SDL has another timing mechanism called timer callbacks. Here we'll be setting a function to be called back after a certain amount of time.|
|Lesson 46|[Multithreading](Multithreading.md)|Multithreading allows your program to do things simultaneously. Here we'll make things print to the console from outside our main thread.|
|Lesson 47|[Semaphores](Semaphores.md)|A major issue in multithreaded applications is that you need to make sure that they don't try to access the same data at the same time. Semaphores are a way to make sure only a certain amount of threads are performing an action at the same time.|
|Lesson 48|[Atomic Operations](Atomic_Operations.md)|Atomic operations are another way to synchronize threads. Here we'll be redoing the previous tutorial with atomic counters.|
|Lesson 49|[Mutexes and Conditions](Mutexes_and_Conditions.md)|Mutexes and conditions are yet another way to synchronize threads. Here we'll be using the added benefit that they allow threads to communicate with each other.|
|Lesson 50|[SDL and OpenGL 2](SDL_and_OpenGL2.md)|SDL is a powerful tool when combined with OpenGL. If you're just starting out with OpenGL or want to maximize compatibility, you can use SDL with OpenGL 2.1.In this tutorial we will make a minimalist OpenGL 2.1 program.|
|Lesson 51|[SDL and Modern OpenGL](SDL_and_Modern_OpenGL.md)|SDL 2.0 now has support for OpenGL 3.0+ with context controls. Here we'll be making a minimalist OpenGL 3+ core program.|
|Lesson 52|[Hello Mobile](Hello_Mobile.md)|Here we'll be loading and displaying an image in our first mobile app!|
|Lesson 53|[Extensions and Changing Orientation](Extensions_and_Changing_Orientation.md)|Here we'll be using SDL extension libraries and handling changing orientation.|
|Lesson 54|[Touches](Touches.md)|Here we'll be handling single touch input.|
|Lesson 55|[Multitouch](Multi_touch.md)|Here we'll be handling multitouch events like pinches and rotation.|
