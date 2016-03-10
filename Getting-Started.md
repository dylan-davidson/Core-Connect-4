Here is the tutorial that you need to setup everything for the Connect 4 project!

## Software Requirements

All team members should install the following software on their computer. Make sure you get started early!

* **Git** - You will be using the command line version of git, which you can install [here](http://git-scm.com/downloads). We will also release a tutorial on how to install and use git shortly.

* **Visual Studio or XCode** - Just like the past projects in this class, you need to use either Visual Studio or XCode to compile and run Connect 4.

## Project Setup for Core

1. In your terminal, go to the location where you wish to put the source code for your project.
2. Clone your team's repository - `git clone https://github.com/eecs183/Connect4_<##>_repository.git`, where `<##>` is the number of your group's repository.
**Be sure to clone your group's repository, NOT the Connect 4 starter code one!**
3. Enter the directory where you cloned the repository: `cd Connect4_<##>_repository`. You should then check to make sure you see the starter code files.
4. Continue the setup by following either the Visual Studio instructions or the XCode instructions below (depending on which IDE you are using).

### Visual Studio

1. Open Visual Studio and select "New Project..."
2. Go to Templates->Visual C++ in the left panel and select "Empty Project" in the middle panel
3. Click on "Browse..." and navigate to the directory where you cloned the starter code
4. Name your project and click OK
5. Right click on "Source Files", go to Add->Existing Item...
6. Navigate to the directory where you cloned the starter code and add **ONLY board.cpp and connect4.cpp**
7. Repeat steps 5 and 6 for the header files, **board.h and connect4.h**
8. Now you can start working on the Core!

### XCode

## Project Setup for Graphics Reach