# Unit Testing is the new Hello World

Suppose you want to implement some sort of function, class, algorithm, or test anything with a library. Or whatever. You can rush and create a ``void main()`` method into a ``main.c`` file, compile, and try it. Or, with very little additional ado, you can build up a unit test.

Why would you build a unit test? Unit testing has the reputation of being boring stuff invented by bored academicians, to entertain over-paid backend developpers working in banking and accounting environments. Well, may be it is true. On the other hand, banking and accounting firms have a clear idea of what is ROI. Unit testing is the single most effective way of developing at a fast pace while keeping a reasonable level of quality in code and design.

I can not put it better than Tim King in his blog entry about [12 benefits of writing unit tests first](http://sd.jtimothyking.com/2006/07/11/twelve-benefits-of-writing-unit-tests-first/).

From my own experience, writing a satisfactory and meaningful unit test is hard when you're not used to it. This tutorial project shows a non-trivial example about an image processor that detects oranges (or orange balls, or anything orange and vaguely round) in the provided pictures:
- The image processor uses an external library, _OpenCV_, to do the hard work.
- To test the image processor you need to access external resources, such as JPG pictures.
- You probably want to be able to see intermediary steps while debugging and tweaking the algorithm.

I stole the algorithm itself from this very good example of [ball tracking with opencv](https://www.pyimagesearch.com/2015/09/14/ball-tracking-with-opencv/).

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
