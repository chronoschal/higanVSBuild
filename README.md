# higanVSBuild
Visual Studio build setup for higan (http://byuu.org)

## Overview
higanVSBuild is a project that provides Visual Studio/MSBuild projects for building the higan emulator project (http://byuu.org). The official higan releases are built with gcc/mingw, so the main purpose of this project is to allow developers to work on and debug higan in Visual Studio before applying their changes to the official source and building with gcc/mingw32. However, the binaries produced by these VS projects can also be used on their own if that is desired.

higanVSBuild does not provide all of the source necessary to build higan; it provides only Visual Studio projects and, if necessary, a patch to apply to the official higan source to allow it to build in VS.

higanVSBuild solutions support configurations for each higan profile (accuracy, balanced, performance).

To stay as close to the official higan build/release as possible, the XP toolchain and XP-compatible SDKs are used where possible.

## Setup
1. Get the higan source release you want to work on.
2. Get the appropriate higanVSBuild release for the official higan source release you want to work on (e.g. v097).
3. Put the VS project directory (e.g. VS2015) at the top level of the source release directory.
4. Apply the source patch to the higan source directory. This can be done using a tool such as patch (available from gnuwin32, http://gnuwin32.sourceforge.net/packages/patch.htm) or TortoiseGitMerge (https://tortoisegit.org/).
5. Get any necessary dependencies (see "Getting dependencies" below).
6. Open higan.sln and develop/build.

### Getting dependencies
The gcc/mingw system that official higan builds use comes with many headers and libraries that are normally provided by separate SDKs (at least when targeting XP). Therefore, it may be necessary to get some additional dependencies before you will be able to build higan using higanVSBuild. Currently, the old DirectX SDK and 7.1 Platform SDK are expected, although it may be possible to use the more modern Windows SDK depending on what your goals are. It may also be necessary to get additional OpenGL headers. Unfortunately, the higanVSBuild projects currently assume the last standalone DirectX SDK relelease (June 2010) is installed in its default location on C:\, so it may be necessary to update this if this isn't the case for you.

Here is a list of dependencies that will likely need to be provided before higan will build in VS:

1. Windows SDK 7.1 (https://www.microsoft.com/en-us/download/details.aspx?id=8279)
2. Direct X SDK June 2010 (https://www.microsoft.com/en-us/download/details.aspx?id=6812)
3. OpenGL headers (like wglext.h) that may not be part of the Windows SDK. (Grab these from the TDM-mingw installation you would normally use to build higan, or grab them from the official OpenGL site.)
