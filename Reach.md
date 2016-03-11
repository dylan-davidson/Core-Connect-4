The following is a list of pre-approved reach features. This list is non-exhaustive. If you wish to do a feature other than one listed on here, or a variation on one listed, you may do so, but you **must** contact us at 183connect4@umich.edu to get your feature _approved_. If you do not contact us to get a non-listed feature approved you will **likely not receive credit**.

## Graphics Using OpenGL

To setup your project for the graphics reach, please follow [these instructions](Getting-Started#project-setup-for-graphics-reach).

OpenGL is an open-source Graphics Library extension of C++. The following functions are located in <code>graphics.cpp</code> and are part of the OpenGL construct. You may modify these functions for your Reach portion.

* <code>void init(void)</code>: Called once at the beginning of the graphics program. Initializes global variables used in other functions.
* <code>void display(void)</code>: This is where the majority of your logic will go. This function is what draws shapes in the window. The distribution code draws a yellow rectangle. Some functions you will need to know in order to draw shapes are:
  * <code>glColor3f()</code>: Sets the color to draw. Takes 3 double arguments within range [0,1] to represent the red, green, and blue components, respectively. Example call to set the color to red: <code>glColor3f(1.0, 0.0, 0.0);</code>
  * <code>drawCircle()</code>: This is not an OpenGL function, but it has been declared and defined for you. It takes two integer coordinates and an integer radius and draws a circle on the screen of the specified radius whose center is at the specified coordinate. All arguments are in pixel units. Example call to draw a circle of radius 25 at coordinate (50,60): <code>drawCircle(50, 60, 25);</code>
  * <code>glRasterPos2i()</code>: Takes two integer coordinates. Used with the next function to write words in the graphics window. This function specifies where to start writing. Example call: <code>glRasterPos2i(200, 150);</code>
  * <code>glutBitmapCharacter()</code>: Specifies font, size, and character to print. **Prints only one character, so if you need to print a longer string then this function will need to be put in a loop**. Example call: <code>glutBitmapCharacter(GLUT_BITMAP_HELVETICA_18, 'A');</code>
  * If you want to draw triangles or rectangles, first type <code>glBegin(GL_TRIANGLES)</code> or <code>glBegin(GL_QUADS)</code>. Then specify the coordinates in groups of three for triangles, or groups of four for rectangles, using the function <code>glVertex2i()</code> that takes two integer coordinates. End with <code>glEnd()</code>. Example calls to draw one triangle:
<pre><code>glBegin(GL_TRIANGLES);
glVertex2i(100, 100);
glVertex2i(150, 100);
glVertex2i(100, 150);
glEnd();</code></pre>
  An example call to draw a rectangle is given in the distribution code.
* <code>void reshape(int w, int h)</code>: This function is called when the user changes the size of the graphics window. It takes two integer arguments representing the new width and height of the window (in pixels).
* <code>void refresh(void)</code>: This function is called at the beginning of the graphics program and when the system is idle.
* <code>void kbd(unsigned char key, int x, int y)</code>: This function is called when the user presses a key on the keyboard. The key is input as a character argument.
* <code>void cursor(int x, int y)</code>: This function is called when the user moves the mouse in the graphics window. The two inputs are the new x and y coordinates of the mouse (in pixels).
* <code>void drag(int x, int y)</code>: This function is called when the user drags the mouse in the graphics window (i.e. the mouse moves and the mouse button is down). The two inputs are the new x and y coordinates of the mouse (in pixels).
* <code>void mouse(int button, int state, int x, int y)</code>: This function is called when the mouse button is pressed or released. The first parameter specifies which mouse button was pressed or released. The second parameter specifies the current state of the button (possible values include GLUT_UP and GLUT_DOWN). The last two parameters are the integer coordinates of the mouse (in pixels).
* <code>int graphicsPlay(int argc, char *argv[])</code>: This function is written for you. It is the first function called and sets up all of the listeners for the mouse and keyboard, creates the graphics window, and initializes and displays the graphics, among other things.

Here is the [grading rubric](Grading#graphics) for graphics

### Recommended Reading

* [An Introduction to OpenGL](http://www.glprogramming.com/red/chapter01.html)

## Artificial Intelligence

Here is the [grading rubric](Grading#artificial_intelligence) for AI

### Easy AI

Our easy AI implementation will implement the following algorithm:

* If the opponent can win in the next turn, we will try to block that move.
* Otherwise, we will place a token in the column that has the fewest number of tokens.

### Recommended Reading

* [Minimax Algorithm](https://en.wikipedia.org/wiki/Minimax)