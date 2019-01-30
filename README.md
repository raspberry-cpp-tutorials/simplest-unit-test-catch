# Unit Testing is the new Hello World

Suppose you want to implement some sort of function, class, algorithm, or test anything with a library. Or whatever. You can rush and create
a ``void main()`` method into a ``main.c`` file, compile, and try it. Or, with very little additional ado, you can build up
a unit test.

Why would you build a unit test, when we all agree that this boring stuff invented by bored academicians only interest insipid 
backend developpers working in banking and accounting environments? Well, apart from being all that, they are also the single most 
effective way of developing at a fast pace while keeping a reasonable level of code and design quality.

The immediate advantage of having one of those unit tests is that it keeps the testing code forever, separated from your code, in a package
that you can compile, debug, use as an example. Later on, when you add more tests, you don't need to remove the existing ones. After
a while, you end up with your code plus a battery of automated checks that will spare you the effort of testing all the basic functionalities
in your application.

The cost of the unit tests is that they have an impact on how you design your applications. But the impact is good. They force you to use
loose coupling and high cohesion, which is nearly the definition of a good design.


# Cross-platform development environment
The project is configured via _cmake_ which makes it compatible with _XCode_, _Code::Build_, _gcc_ and other development tools, and this is what you need to do from either a _Mac OS X Terminal_, a _Linux Terminal_ or a _MinGW Terminal_:

```Bash
cd ~/to/your/working/folder
git clone https://github.com/raspberry-cpp-tutorials/simplest-unit-test-catch.git
cd simplest-unit-test-catch
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Debug ../src
ctest --output-on-failure
```

To run the application:

```Bash
ctest
```

There are more detailed instructions to install a working development environment in the three major operative systems:

* [Installing Mac OS X development environment](https://github.com/raspberry-cpp-tutorials/gtk-opencv-simple/wiki/Mac-OS-X-development-environment)
* [Installing Windows development environment](https://github.com/raspberry-cpp-tutorials/gtk-opencv-simple/wiki/Windows-development-environment)
* [Installing Linux development environment](https://github.com/raspberry-cpp-tutorials/gtk-opencv-simple/wiki/Linux-development-environment)

# The project's folder structure

There are several great articles that discuss about the best folder structure for a project built with _CMake_:

 * [https://arne-mertz.de/2018/06/cmake-project-structure/](https://arne-mertz.de/2018/06/cmake-project-structure/): I like this one because it discusses how to integrate those header-only libraries, and uses _Catch_ as an example.
 * [https://rix0r.nl/blog/2015/08/13/cmake-guide/](https://rix0r.nl/blog/2015/08/13/cmake-guide/): I like this one because it shows in detail how to configure CMake and why, and also acknowledges the difference between library (which is easily unit tested) and application (which is the user interface, and not very easy to unit test).

This project is an example of what might look any project at early stages. There are ``cpp`` and ``hpp`` folders for the _C++_ code and headers, and then there is the test folder. The test folder contains some resources to use during the tests:

```
.gitignore        <-- Ignore xcode, codeb, build folders.
/src              <-- All sources are here
   CMakeList.txt  <--- The top CMake configuration file.
   /cpp        <-------- C++ source files.
   /hpp        <-------- C++ header files.
   /tst        <-------- Unit tests
      /res     <-------- Resources for unit tests.
/build            <-- Contains the temporary build files. 
                      Not under version control
/xcode            <-- Contains the XCode project.
                      Not under version control.
/codeb            <-- Contains the Code::Blocks project. 
                      Not under version control. 
```
