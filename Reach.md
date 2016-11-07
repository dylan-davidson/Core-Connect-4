The following is a list of pre-approved reach features. This list is non-exhaustive. If you wish to do a feature other than one listed on here, or a variation on one listed, you may do so, but you **must** contact us at 183connect4@umich.edu to get your feature _approved_. If you do not contact us to get a non-listed feature approved you will **likely not receive credit**.

You may modify the Board class for the Reach portion of the project. Make sure you save the Core implementation in a different git branch using the instructions that were given. You should save a backup copy for yourself, as well.

## Graphics Using OpenGL

The Core version of the project included a basic GUI interface using OpenGL (<code>graphics.h</code> and <code>graphics.cpp</code> files). One option for your reach is to create a unique look and feel for your game's GUI by expanding the basic graphics. To setup your project for using graphics, please follow [these instructions](Getting-Started#project-setup-for-graphics).

OpenGL is an open-source Graphics Library extension of C++. The following functions are located in <code>graphics.cpp</code> and are part of the OpenGL construct. You may modify these functions for your Reach portion.

* <code>void init(void)</code>: Called once at the beginning of the graphics program. Initializes global variables used in other functions. Note that the lower left corner of the window is where the coordinate (0,0) is located, with x-coordinates increasing as you move right and y-coordinates increasing as you move up.
* <code>void display(void)</code>: This is where the majority of your logic will go. This function is called often, every time the mouse moves or a keyboard key is pressed, and even when the system is idle. This is the function that draws shapes in the window. The distribution code draws a yellow rectangle. Some functions you will need to know in order to draw shapes are:
  * <code>glColor3f()</code>: Sets the color to draw. Takes 3 double arguments within range [0,1] to represent the red, green, and blue components, respectively. Example call to set the color to red: <code>glColor3f(1.0, 0.0, 0.0);</code>
  * <code>drawCircle()</code>: This is not an OpenGL function, but it has been declared and defined for you. It takes two integer coordinates and an integer radius and draws a circle on the screen of the specified radius whose center is at the specified coordinate. All arguments are in pixel units. Example call to draw a circle of radius 25 at coordinate (50,60): <code>drawCircle(50, 60, 25);</code>
  * <code>glRasterPos2i()</code>: Takes two integer coordinates. Used with the next function to write words in the graphics window. This function specifies where to start writing. Example call: <code>glRasterPos2i(200, 150);</code>
  * <code>glutBitmapCharacter()</code>: Specifies font, size, and character to print. **Prints only one character, so if you need to print a longer string then this function will need to be put in a loop**. See this [documentation](https://www.opengl.org/documentation/specs/glut/spec3/node76.html) for the full list of valid parameters. Example call: <code>glutBitmapCharacter(GLUT_BITMAP_HELVETICA_18, 'A');</code>
  * If you want to draw triangles or rectangles, first type <code>glBegin(GL_TRIANGLES)</code> or <code>glBegin(GL_QUADS)</code>. Then specify the coordinates in groups of three for triangles, or groups of four for rectangles, using the function <code>glVertex2i()</code> that takes two integer coordinates. The <code>2</code> in the function name means two points will be used (as we are working in a 2-dimensional space), and the <code>i</code> in the function name stands for integer. Other forms, including floating-point values, are also possible. See this [documentation](https://www.opengl.org/sdk/docs/man2/xhtml/glVertex.xml) for more information. End with <code>glEnd()</code>. Example calls to draw one triangle:
<pre><code>glBegin(GL_TRIANGLES);
glVertex2i(100, 100);
glVertex2i(150, 100);
glVertex2i(100, 150);
glEnd();</code></pre>
  An example call to draw a rectangle is given in the distribution code. For more information on drawing shapes, check out this [tutorial](http://www.falloutsoftware.com/tutorials/gl/gl2p5.htm).
* <code>void reshape(int w, int h)</code>: This function is called when the user changes the size of the graphics window. It takes two integer arguments representing the new width and height of the window (in pixels).
* <code>void refresh(void)</code>: This function is called at the beginning of the graphics program and when the system is idle.
* <code>void kbd(unsigned char key, int x, int y)</code>: This function is called when the user presses a key on the keyboard. The key is input as a character argument.
* <code>void cursor(int x, int y)</code>: This function is called when the user moves the mouse in the graphics window. The two inputs are the new x and y coordinates of the mouse (in pixels).
* <code>void drag(int x, int y)</code>: This function is called when the user drags the mouse in the graphics window (i.e. the mouse moves and the mouse button is down). The two inputs are the new x and y coordinates of the mouse (in pixels).
* <code>void mouse(int button, int state, int x, int y)</code>: This function is called when the mouse button is pressed or released. The first parameter specifies which mouse button was pressed or released. The second parameter specifies the current state of the button (possible values include <code>GLUT_UP</code> and <code>GLUT_DOWN</code>). The last two parameters are the integer coordinates of the mouse (in pixels).
* <code>int graphicsPlay(int argc, char *argv[])</code>: This function is written for you. It is the first function called and sets up all of the listeners for the mouse and keyboard, creates the graphics window, and initializes and displays the graphics, among other things.

Here are some helpful hints to get you started:
* Read through the distribution code in <code>graphics.h</code> and <code>graphics.cpp</code>. If you do not understand what a function does, reread the description above.
* <code>display()</code> is the only function that actually draws to the screen. Do not try to draw shapes from any other function. The other functions will change data, which should in turn change what is drawn from <code>display()</code>.
* Fun fact: GLUT stands for OpenGL Utility Toolkit. It is what allows you to create a display window for drawing your graphics!
* If you are trying to find the right color to display, check out this [link](https://tug.org/pracjourn/2007-4/walden/color.pdf) that lists all the colors you can get from incrementing the red, green, and blue values by 0.1 (within the range [0,1]).
* Once you get the basic functionality of Connect 4 working with graphics and you are wondering how you can extend it to make it your own, take a look at the functions you haven't used yet and think about how you can add them to your project. Also, take a look at the grading rubric for suggestions on possible extensions.

Here is the [grading rubric](Grading#graphics) for graphics

### Recommended Reading

* [An Introduction to OpenGL](http://www.glprogramming.com/red/chapter01.html)

## Artificial Intelligence

> Another option for you Reach is to implement an AI player for your game. To setup your project for the AI reach, please follow [these instructions](Getting-Started#project-setup-for-ai-reach). 

This project includes an object file called driver that will run a main function. It allows the user to play against the AI you implement. Recall from lecture that all source files (*.cpp files) are compiled into object files before linking together to form an executable that you can run. The driver object file included in the project will link with the object files created from compiling <code>board.cpp</code> and <code>ai.cpp</code> to create the executable.

For the AI Reach project, you will need to create an algorithm to choose a column given an instance of the Board class. You can create as many helper functions as you want, but we will only be grading based on the return value of <code>int connect4AI(const Board& board);</code> in <code>ai.cpp</code>. This function must return an integer in the range [0,NUM_COLS-1].

When you run your program, the user and the AI will alternate moves. The user will move first, being prompted for an input. If the user enters a legal move, the board will print with the user's move and will print again with the AI's move. This will repeat until the game ends or the user quits.

**Your implementation must take less than 2 seconds to decide on a move.** To calculate the time your function takes, you can use a C++ [clock](http://www.cplusplus.com/reference/ctime/clock/). Here is how to implement it:  
1. <code>#include &lt;time.h&gt;</code> or <code>#include &lt;ctime&gt;</code> in <code>ai.cpp</code>.  
2. <code>#include &lt;iostream&gt;</code> in <code>ai.cpp</code>.  
3. Write <code>using namespace std;</code> in <code>ai.cpp</code>.  
4. At the beginning of your <code>connect4AI</code> function, declare an instance of the clock class and initialize it to the current time:  <pre><code>clock_t t;
t = clock();</code></pre>
5. After your calculations (but before you return from the function), calculate the difference in time and print it out as seconds:
<pre><code>t = clock() - t;
cout &lt;&lt; "Took " &lt;&lt; double(t) / CLOCKS_PER_SEC &lt;&lt; " seconds" &lt;&lt; endl;</code></pre>
Make sure you **remove all print (cout) statements before handing in your implementation**. The final version of your function should not print anything. These examples are for your own use during implementation. They are not to be included in the final product.

Here are some helpful hints to get your started:
* Play the Core a handful of times with different people. Pay attention to what moves you and your opponent make and think about why those moves are chosen. Notice any patterns in behavior. Ask your opponent why they chose a move you don't understand.
* Categorize moves (a win, a block, etc.). Under what conditions is a move preferable? 
* Can you think of cases when multiple columns might be equally preferable? What is your strategy in those cases? For example, think about the first move of the game. You start with an empty board. How do you choose a column to place your initial token?
* Develop a strategy of gameplay (or multiple strategies! An offensive strategy, a defensive strategy, a greedy strategy, a hybrid strategy, etc.).
* Implement your strategy (or strategies).
* Test your implementations. Play against your AI. How does your AI perform? Can you beat it? Where does it go wrong?
* Improve your implementation. Tweak it. Play with it. See what happens. Have fun with it!

Here is the [grading rubric](Grading#artificial_intelligence) for AI

### Easy AI

Our easy AI implementation will select a random column to use as its move. This is the AI included in the distribution code.