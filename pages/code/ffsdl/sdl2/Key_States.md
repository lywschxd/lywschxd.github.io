# Lazy Foo' Productions


# Key States

![](images/preview-17.png)

As we saw in the [mouse input tutorial](index-17.php.htm), there are ways to get the state of the input devices (mouse, keyboard,
etc) other than using events. In this tutorial, we'll be remaking the [keyboard input tutorial](index-4.php.htm) using key states
instead of events.
```cpp
      //Main loop flag
bool quit = false;
//Event handler
SDL_Event e;
//Current rendered texture
LTexture* currentTexture = NULL;
```
Right before we enter the main loop, we declare a texture pointer to keep track of which texture we're rendering to the screen.
```cpp
         //While application is running
while( !quit )
{
//Handle events on queue
while( SDL_PollEvent( &e ) != 0 )
{
//User requests quit
if( e.type == SDL_QUIT )
{
quit = true;
}
}
```
As you can see, we aren't checking for key events in the event loop. All our keyboard input is going to be handled with key states.

One important thing to know about how SDL handles key states is that you still need an event loop running. SDL's internal keystates are updated every time
[SDL_PollEvent]http://wiki.libsdl.org/SDL_PollEvent) is called, so make sure you polled all events on queue before checking key states.
```cpp
        //Set texture based on current keystate
const Uint8* currentKeyStates = SDL_GetKeyboardState( NULL );
if( currentKeyStates[ SDL_SCANCODE_UP ] )
{
currentTexture = &gUpTexture;
}
else if( currentKeyStates[ SDL_SCANCODE_DOWN ] )
{
currentTexture = &gDownTexture;
}
else if( currentKeyStates[ SDL_SCANCODE_LEFT ] )
{
currentTexture = &gLeftTexture;
}
else if( currentKeyStates[ SDL_SCANCODE_RIGHT ] )
{
currentTexture = &gRightTexture;
}
else
{
currentTexture = &gPressTexture;
}
```
Here we set our texture that's going to be rendered. First we get a pointer to the array of key states using
[SDL_GetKeyboardState](http://wiki.libsdl.org/SDL_GetKeyboardState). The state of all the keys are ordered by
[SDL_Scancode](http://wiki.libsdl.org/SDL_Scancode). Scan codes are like the
[SDL_Keycode](http://wiki.libsdl.org/SDL_Keycode) values, only scan codes are designed to work with international keyboards. Depending on the keyboard
layout, different letters might be in different places. Scan codes go off default physical position of the keys as opposed to where they might be on a specific keyboard.

All you have to do check if a key is down is to check its state in the key state array. As you can see in the above code, if the key is down we set the current texture to the
corresponding texture. If none of the keys are down, we set the default texture.
```cpp
         //Clear screen
SDL_SetRenderDrawColor( gRenderer, 0xFF, 0xFF, 0xFF, 0xFF );
SDL_RenderClear( gRenderer );
//Render current texture
currentTexture->render( 0, 0 );
//Update screen
SDL_RenderPresent( gRenderer );
}
}
}
```
Finally here we render the current texture to the screen.

Download the media and source code for this tutorial [here](zip/18_key_states.zip).
