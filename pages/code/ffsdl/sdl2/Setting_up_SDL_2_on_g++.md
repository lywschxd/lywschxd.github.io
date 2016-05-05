
# Lazy Foo' Productions

# Setting up SDL 2 on g++

[1)](#1)Go download the [source for lesson 01](zip/01_hello_SDL.zip). Extract the source somewhere. Now compile by entering this command:
```bash
 g++ 01_hello_SDL.cpp -w -lSDL2 -o 01_hello_SDL
```
Now you may get an error saying it can't find SDL.h. For linux, we'll have to include the SDL headers like this:
```cpp
 #include<SDL2/SDL.h>
```
As the programs get bigger and bigger, having to manually punch in this compilation command gets very tedious very quickly. This is why I recommend using Make.

[2)](#2) GNU Make allows you to make build scripts that'll automate the compilation process.
From Basic Makefile
```bash
#OBJS specifies which files to compile as part of the project
OBJS = 01_hello_SDL.cpp
#OBJ_NAME specifies the name of our exectuable
OBJ_NAME = 01_hello_SDL
#This is the target that compiles our executable
all : $(OBJS)
g++ $(OBJS) -w -lSDL2 -o $(OBJ_NAME)
```
Here we have a basic Makefile. At the top we declare and set the "OBJS" macro which specifies which files we're compiling. Then we set the "OBJ_NAME" macro that specifies
the name of our executable.

After setting these two macros, we have the "all" target which compiles the program. It's followed by the dependencies which as you can see is the OBJS macro, because
obviously you need the source files to compile the program.

After specifying the name of the target and its dependencies, the command to create the target is on the next line. **The command to create the target must begin with a
tab or Make will reject it**.

As you would expect, the command to compile the program is largely the same as the command we would compile it off the command line. A key difference is that we have
macros that we insert into the command which makes things like adding new files to the project must easier since you only have to change the macro as opposed to changing
the whole command.

In future tutorials, we will be using more libraries. We should probably use more macros to make the process of adding them easier.
From Makefile
```bash
#OBJS specifies which files to compile as part of the project
OBJS = 01_hello_SDL.cpp
#CC specifies which compiler we're using
CC = g++
#COMPILER_FLAGS specifies the additional compilation options we're using
# -w suppresses all warnings
COMPILER_FLAGS = -w
#LINKER_FLAGS specifies the libraries we're linking against
LINKER_FLAGS = -lSDL2
#OBJ_NAME specifies the name of our exectuable
OBJ_NAME = 01_hello_SDL
#This is the target that compiles our executable
all : $(OBJS)
$(CC) $(OBJS) $(COMPILER_FLAGS) $(LINKER_FLAGS) -o $(OBJ_NAME)
```
Now our compilation command is much more flexible.

Near the top we have the macros that define the files we're compiling and the compiler we're using.

The "COMPILER_FLAGS" macro are the additional options we use when compiling. In this case we're disabling all warnings. The
"LINKER_FLAGS" macro specifies which libraries we're linking against. Here we're compiling against SDL2\. Notice how there's a **-l**
flag before the library.

Finally at the bottom we have our target compiling using all of our macros. Thanks to macros we can very easily change the macros to add more files and libraries as we
need them.

Save this Makefile code to a file named "Makefile" (case sensitive with no file extension) or you can use the one I premade [here](http://lazyfoo.net/tutorials/SDL/01_hello_SDL/linux/cli/Makefile).
Open a command line in the directory with the source files and run the command **make all**. Make will search for a file named "Makefile" in the directory
Make was called in and run the Makefile that will compile your code.

Now that you have SDL2 compiling, it time to go onto part 2 of the tutorial.
[Hello SDL Part 2: Your First Graphics Window](hellosdlc.md)
