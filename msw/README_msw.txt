BUILDING and INSTALLING TreeMaker 5.0 for MS Windows 9x, Me, NT, 2000, XP, 2003
  by Wlodzimierz 'ABX' Skiba

1. INTRODUCTION

This file describes the basic procedures for building from source, installing
and running TreeMaker 5.0 for Windows (TM5W for short). It is not needed for
installing and using a TM5W binary bundle.

This and all other files in this directory are subject to the same license
conditions mentioned in the Source/README.txt file, here referred to as the
main README.

Windows is a registered trademark of Microsoft Corp.

2. BEFORE YOU START

Requisites for building TM5W:
- TreeMaker 5.0 requisites (see main README)
- One of MS Windows 9x, Me, NT, 2000, XP, 2003 
- MinGW driven from Windows console (not MSYS)
- wxWidgets (TM5W was tested with the wxMSW version), as described below

TM5W was mainly developed and tested on Windows 2000 and XP SP2. TM5W should
work on other MS Windows flavours thanks to using wxWidgets toolkit.

3. TreeMaker CONFIGURATIONS

TM5W build was tested in two major configurations, debug and release, but there
is the possibility of mixing build settings into more combinations. 

with "WX_DEBUG=0 TMBUILD=release" : production version
with "WX_DEBUG=1 TMBUILD=debug"   : development version

There are more options and some are related to the wxWidgets build. They are
all listed in the beginning of msw/makefile.gcc file together with a short
description.

4. BUILDING AND INSTALLING TM5W FROM SOURCE

4.1. Compiling wxWidgets

TreeMaker 5.0's user interface uses the multiplatform open-source
library wxWidgets. For maximum portability, TM5W is statically linked.
The complete command used to build wxWidgets for release of TM5W was:

mingw32-make.exe -f makefile.gcc SHARED=0 RUNTIME_LIBS=static UNICODE=1 MONOLITHIC=0 BUILD=release

Note that not all features of wxWidgets are used in TM5W. Unused features can
be turned off before a wxWidgets rebuild. This is done by providing a modified
setup0.h. After obtaining a fresh wxWidgets copy, this file should be copied
from msw/setup0.h to wxWidgets/include/wx/msw/setup0.h path.

4.2. Configuring your Build

Building TM5W requires the environment variable WXWIN pointing to wxWidgets path.

4.3. Building TreeMaker

The complete command used to build wxWidgets for release of TM5W was:

mingw32-make.exe -f makefile.gcc WX_SHARED=0 WX_UNICODE=1 WX_DEBUG=0 PROFILE=0 TMBUILD=release

This command will create a subdirectory in the msw directory of TM5W and will
create there 5 command line test tools and the main executable.

4.4 Installing TreeMaker

You can run TM5W from any path (including the subdirectory where it was
created) but you need to put in the same directory the splash screen, zip
archive with help files, and the about page. They are all located under Source
directory of TM5W and need to be copied into the executable path.

4.5. Building a Distribution Bundle

The Windows installer is made with Inno Setup, which is available at
http://www.jrsoftware.org/isinfo.php . The required script is located in
msw/treemaker.iss. Also, the mingwm10.dll runtime library from MinGW is
required for running the executable.
