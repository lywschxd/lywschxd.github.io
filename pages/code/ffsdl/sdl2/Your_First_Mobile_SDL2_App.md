# Lazy Foo' Productions


# Hello Mobile: Your First Mobile SDL 2 App

![](images/preview-49.png)

Now that you covered the hard part of getting the application to compile and run, let's go over the application code.
```cpp
//Screen dimensions
SDL_Rect gScreenRect = { 0, 0, 320, 240 };
```
Since mobile devices vary a lot in resolution, we're going to use variable screen dimensions instead of constant ones.
```cpp
        //Get device display mode
SDL_DisplayMode displayMode;
if( SDL_GetCurrentDisplayMode( 0, &displayMode ) == 0 )
{
gScreenRect.w = displayMode.w;
gScreenRect.h = displayMode.h;
}
//Create window
gWindow = SDL_CreateWindow( "SDL Tutorial", SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED, gScreenRect.w, gScreenRect.h, SDL_WINDOW_SHOWN );
if( gWindow == NULL )
{
SDL_Log( "Window could not be created! SDL Error: %sn", SDL_GetError() );
success = false;
}
```
Here we call [SDL_GetCurrentDisplayMode](http://wiki.libsdl.org/SDL_GetCurrentDisplayMode) to get the resolution of the mobile device. We then create a window using the device dimensions.

Notice how we're using [SDL_Log](http://wiki.libsdl.org/SDL_Log) instead of printf. This is because Android/iOS have their own platform specific ways to print to the console and SDL gives us a nice
wrapper to make our code cross platform.
```cpp
int main( int argc, char* args[] )
{
//Start up SDL and create window
if( !init() )
{
SDL_Log( "Failed to initialize!n" );
}
else
{
//Load media
if( !loadMedia() )
{
SDL_Log( "Failed to load media!n" );
}
else
{
//Main loop flag
bool quit = false;
//Event handler
SDL_Event e;
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
//Clear screen
SDL_SetRenderDrawColor( gRenderer, 0xFF, 0xFF, 0xFF, 0xFF );
SDL_RenderClear( gRenderer );
//Render splash
gSplashTexture.render( ( gScreenRect.w - gSplashTexture.getWidth() ) / 2, ( gScreenRect.h - gSplashTexture.getHeight() ) / 2 );
//Update screen
SDL_RenderPresent( gRenderer );
}
}
}
//Free resources and close SDL
close();
return 0;
}
```
Other than the fact that we're using SDL_Log, the code is pretty much the same as before.

Download the media and source code for this tutorial [here](zip/52_hello_mobile.zip).
