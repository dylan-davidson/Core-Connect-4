Here is the tutorial that you need to setup everything for the Connect 4 project!

## Software Requirements

All team members should install the following software on their computer. Make sure you get started early!

* **Git** - You will be using the command line version of git, which you can install [here](http://git-scm.com/downloads). We will also release a tutorial on how to install and use git shortly.

* **Visual Studio or XCode** - Just like the past projects in this class, you need to use either Visual Studio or XCode to compile and run Connect4.

## Project Setup for Core

1. In your terminal, go to the location where you wish to put the source code for your project.
2. Clone your team's repository - `git clone https://github.com/eecs183/Connect4_<##>_Repository.git`, where `<##>` is the number of your group's repository.
**Be sure to clone your group's repository, NOT the Connect 4 starter code one!**
3. Enter the directory where you cloned the repository: `cd Connect4_<##>_Repository`. You should then check to make sure you see the starter code files.
4. Continue the setup by following either the Visual Studio instructions or the XCode instructions below (depending on which IDE you are using).

### Visual Studio

**Make sure that your project is named Connect4**

1. Open Visual Studio and select "New Project..."
2. Go to Templates->Visual C++ in the left panel and select "Empty Project" in the middle panel
3. Click on "Browse..." and navigate to the directory where you cloned the starter code
4. **Name your project as Connect4** and click OK
5. Right click on "Source Files", go to Add->Existing Item...
6. Navigate to the directory where you cloned the starter code and add **ONLY board.cpp, connect4.cpp and main.cpp**
7. Repeat steps 5 and 6 for the header files, **board.h and connect4.h**
8. Now you can start working on the Core!

### XCode

**Make sure that your project is named Connect4**

1. Open XCode and select "Create a new Xcode project"
2. Go to OS X->Application in the left panel, select "Command Line Tool" in the middle panel, and click "Next"
3. **Enter the Product Name as Connect4**, make sure Language is C++, and click "Next"
4. Navigate to the directory where you cloned the starter code and click "Create"
5. Right click on main.cpp, select "Delete", and select "Move to Trash"
6. Go to "Finder", navigate to the directory where you cloned the starter code, and drag **board.h, board.cpp, connect4.h, connect4.cpp and main.cpp** into the project
7. Make sure "Copy items if needed" is **unchecked** and click "Finish"
8. Now you can start working on the Core!

## Project Setup for Graphics

### Visual Studio

1. Inside the directory where you cloned the starter code, you will find a folder called "glut", which contains three files: "glut.h", "glut32.dll" and "glut32.lib".
2. Go to "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\" and create a folder called "GL" if it does not already exist.
3. Copy "glut.h" into the "GL" folder you just created ("C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\GL\")
4. Copy "glut32.dll" into "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\"
5. Copy "glut32.lib" into "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\lib\"
6. Open your Connect 4 project in Visual Studio and add **both graphics.cpp and graphics.h** into the project the same way the other starter files were added in the Core
7. In main.cpp, comment out line 21: `cout << "Under construction..." << endl;` and **uncomment** line 22: `graphicsPlay(argc, argv);`
8. On line 2, add `#include "graphics.h"`
9. Have fun with the graphics reach!

### XCode

1. Open your Connect 4 project in XCode and add **both graphics.cpp and graphics.h** into the project
2. Double click on the blue project icon in the left panel
3. Click the "Build Phases" tab, open the "Link Binary With Libraries" list, and click the '+' sign at the bottom left corner of the list
4. Add both "OpenGL.framework" and "GLUT.framework"
5. In main.cpp, comment out line 21: `cout << "Under construction..." << endl;` and **uncomment** line 22: `graphicsPlay(argc, argv);`
6. On line 2, add `#include "graphics.h"`
7. Have fun with the graphics reach!

## Project Setup for AI Reach

### Visual Studio

1. Open your Connect 4 project in Visual Studio and add **ai.h** into the project the same way the other header files were added in the core
2. Now add **ai.cpp and driver-vs.o** into the project the same way the other source files were added in the core

#### To Use driver-vs.o’s Main

1. Right click on your **connect4.cpp** file in the left panel and select "Properties".
2. Under the "General" tab, choose "Yes" for the "Excluded From Build" option and click "OK".
3. Right click on your **driver-vs.o** file in the left panel and select "Properties".
4. Under the "General" tab, choose "No" for the "Excluded From Build" option and click "OK".

#### To Revert Back To connect4.cpp’s Main

1. Right click on your **driver-vs.o** file in the left panel and select "Properties".
2. Under the "General" tab, choose "Yes" for the "Excluded From Build" option and click "OK".
3. Right click on your **connect4.cpp** file in the left panel and select "Properties".
4. Under the "General" tab, choose "No" for the "Excluded From Build" option and click "OK".

### XCode

1. Open your Connect 4 project in XCode and add **ai.h, ai.cpp, and driver-xcode.o** into the project the same way the other starter files were added in the core

#### To Use driver-xcode.o’s Main

1. Click on your **connect4.cpp** file in the left panel.
2. **Uncheck** the project name under "Target Membership" in the right panel.
3. Click on your **driver-xcode.o** file in the left panel.
4. **Check** the project name under "Target Membership" in the right panel.

#### To Revert Back To connect4.cpp’s Main

1. Click on your **driver-xcode.o** file in the left panel.
2. **Uncheck** the project name under "Target Membership" in the right panel.
3. Click on your **connect4.cpp** file in the left panel.
4. **Check** the project name under "Target Membership" in the right panel.