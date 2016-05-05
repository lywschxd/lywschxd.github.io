# Lazy Foo' Productions

# Setting up SDL on Windows

**An important note for Microsoft Windows developers:**

As part of your set up process, you are going to have to place the dll file some place where your program can link with it during runtime. You can either put the dll
file in the same directory as your executable, or put it in the system directory. C:WINDOWSSYSTEM32 is the 32bit windows system directory and C:WindowsSysWOW64 is
the 64bit system directory of 32bit applications.

The advantages of placing the dll file in the system directory are:
1.  Your operating system will always be able to find the library on your system, so you can compile and run dynamically linked applications anywhere on your system
2.  You won't have to place a copy of the dll file with every single application you develop

With that in mind, when distributing your application you should never mess with the user's system directory. The user could have applications that require SDL
version ABC in the system directory and you could be overwriting it with SDL version XYZ. Your distribution version should have the dll files in the same
directory as the executable.
Select Your IDE/Compiler

|icon|IDE/Compiler|
|----|:----------:|
|[![](images/logo-9.png)](index-71.php.htm)|[Code::Blocks 12.11](index-71.php.htm)|
|[![](images/logo-10.png)](index-72.php.htm)|[Visual Studio.NET 2010 Ultimate](index-72.php.htm)|
|[![](images/logo-11.png)](hellosdl_windows_mingw.md)|[Command Line (MinGW)](hellosdl_windows_mingw.md)|

[Back](index.md)
