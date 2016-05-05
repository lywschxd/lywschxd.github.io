# SDL2环境搭建

## windows Mingw 环境搭建
### MinGW 环境配置
1. 下载MinGw，并添加到环境变量中
2. 下载[SDL开发包](http://libsdl.org/download-2.0.php)
3. 可以参考[这里](http://lazyfoo.net/tutorials/SDL/01_hello_SDL/windows/mingw/index.php)进行Makefile的编写
    ```
    #OBJS specifies which files to compile as part of the project
    OBJS = hello_SDL.cpp
    
    #CC specifies which compiler we're using
    CC = g++
    
    #INCLUDE_PATHS specifies the additional include paths we'll need
    INCLUDE_PATHS = -Iinclude
    
    #LIBRARY_PATHS specifies the additional library paths we'll need
    LIBRARY_PATHS = -Llib
    
    #COMPILER_FLAGS specifies the additional compilation options we're using
    # -w suppresses all warnings
    # -Wl,-subsystem,windows gets rid of the console window
    COMPILER_FLAGS = -w -Wl,-subsystem,windows
    
    #LINKER_FLAGS specifies the libraries we're linking against
    LINKER_FLAGS = -lmingw32 -lSDL2main -lSDL2
    
    #OBJ_NAME specifies the name of our exectuable
    OBJ_NAME = 01_hello_SDL
    
    #This is the target that compiles our executable
    all : $(OBJS)
    	$(CC) $(OBJS) $(INCLUDE_PATHS) $(LIBRARY_PATHS) $(COMPILER_FLAGS) $(LINKER_FLAGS) -o $(OBJ_NAME)
    ```
4. 在终端运行mingw32-make.exe来编译。


### MinGW 扩展库 环境配置
#### 图片库
1. 下载[SDL扩展库](https://www.libsdl.org/projects/SDL_image/)
2. 拷贝include目录和库
3. 可以参考[这里](http://lazyfoo.net/tutorials/SDL/06_extension_libraries_and_loading_other_image_formats/windows/mingw/index.php)进行Makefile的编写
    ```
    #OBJS specifies which files to compile as part of the project
    OBJS = 06_extension_libraries_and_loading_other_image_formats.cpp
    
    #CC specifies which compiler we're using
    CC = g++
    
    #INCLUDE_PATHS specifies the additional include paths we'll need
    INCLUDE_PATHS = -IC:\mingw_dev_lib\include\SDL2
    
    #LIBRARY_PATHS specifies the additional library paths we'll need
    LIBRARY_PATHS = -LC:\mingw_dev_lib\lib
    
    #COMPILER_FLAGS specifies the additional compilation options we're using
    # -w suppresses all warnings
    # -Wl,-subsystem,windows gets rid of the console window
    COMPILER_FLAGS = -w -Wl,-subsystem,windows
    
    #LINKER_FLAGS specifies the libraries we're linking against
    LINKER_FLAGS = -lmingw32 -lSDL2main -lSDL2 -lSDL2_image
    
    #OBJ_NAME specifies the name of our exectuable
    OBJ_NAME = 06_extension_libraries_and_loading_other_image_formats
    
    #This is the target that compiles our executable
    all : $(OBJS)
    	$(CC) $(OBJS) $(INCLUDE_PATHS) $(LIBRARY_PATHS) $(COMPILER_FLAGS) $(LINKER_FLAGS) -o $(OBJ_NAME)
    ```
我们可以使用`-lSDL2_image`, `-lSDL2_ttf`, `-lSDL2_mixer`来load不同的库。

#### 字体库
使用如图片库一样，可以从[这里](https://www.libsdl.org/projects/SDL_ttf/)下载

#### SDL_mixer库
SDL_mixer是sdl用来播放声音的，配置和其他库一样，可以从[这里](https://www.libsdl.org/projects/SDL_mixer/)下载