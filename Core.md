The goal of the Core is to implement a fully-functioning game of Connect 4. The game will be played in the terminal window with two players manually entering their moves. The program will check for a win or draw after every move. Below we will outline the game, the functions involved in the implementation, and a few sample runs of the fully-implemented program.

The files included in this project are listed below.
* **board.h**: Declarations of global constant variables, functions for the Board class, and enums used throughout the project. Enumerators, also known as 'enums', are explained below for you.
* **board.cpp**: Definitions of Board member functions. The two member functions <code>prettyPrintBoard</code> and <code>atLocation</code> are already defined for you. You will need to define the rest.
* **connect4.h**: Declarations of functions to read a board from a file and to write a board to a file along with the function that facilitates playing via terminal (console). 
* **connect4.cpp**: Definitions of the functions in connect4.h. You need to define all of these. The cout statements are included in the distribution code.
* **main.cpp**: Definition of the main function. You will only have to update this function if you choose to implement the graphics reach for the project.

* **test_board.cpp**: Definition of a test suite for the Board class. We highly suggest you use this test suite to implement your own test cases and validate that your Board functions comply with their respective RMEs. 

* **graphics.h**: Declarations of functions used for the graphics part of the project.
* **graphics.cpp**: Partial definitions of functions in graphics.h and the main function that runs the interface. The graphics starter code gives a basic graphical interface that you can play the game through. See [Reach section](Reach) for more details on editing the existing functions to develop your own look and feel for your program.

There are three Sample Runs included in the distribution code, as well as files that will be needed for the Reach portion of the project. Make sure to include the six files listed above in Visual Studio or Xcode and follow [these instructions](Getting-Started#project-setup-for-graphics) carefully to setup the graphics correctly.  

## How to Play Connect 4
Connect 4 is a two-player game which takes place on a 6 x 7 rectangular board. Player 1 has 21 'x' tokens and Player 2 has 21 'o' tokens. Each player can drop a token at the top of the board in one of the seven columns; the token falls down and fills the lowest unoccupied square. A player cannot drop a token in a column if it is already full (i.e. it already contains six tokens).

The game board cells will be labeled as follows:  
<pre><code>
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
col 1   2   3   4   5   6   7  
</code></pre>

The object of the game is to connect four tokens vertically, horizontally, or diagonally. If the board is filled and no one has aligned four tokens then the game is a draw (i.e. no one wins after 42 moves).

Note: Within the array, the rows are numbered in ascending order from bottom to top, i.e., the lowest numbered row is on the bottom and the highest numbered row is on the top. Internally, this puts data[0][0] at the lower-left hand corner.

Note: We display column numbers starting at 1, but these are for display only. Internally, indexing begins at 0.

## Specifications
The game begins by asking if you wish to load a game or to play a game. This entry is not case-sensitive. An uppercase 'P' or a lowercase 'p' will both mean "play".

<pre><code>Enter L to load a game, or P to play:</code> <u>p</u></pre>

**Play**: If "play" is chosen, the game will ask for the names of two players.  
<pre><code>Player 1, enter your name:</code> <u>Batman</u>  
<code>Player 2, enter your name:</code> <u>Bane</u></pre>  

It will then print the initial board and ask for a move from the first player.
<pre><code>
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
  |   |   |   |   |   |   |   |  
  +---+---+---+---+---+---+---+  
col 1   2   3   4   5   6   7  

Enter: the column to move, q to quit, s to save  
Batman enter your move:  
</code></pre>

See the next section on rules of play.

**Load a game**: If "play" is not chosen, all other entries will load a game from a file. It will open the file given, read it, and load the board accordingly. The board is then displayed. This file will be a .txt file with the following format:
<pre><code>name of player 1
name of player 2
a FEN string holding all board information
</code></pre>

For details of FEN strings, see a later section on FEN string.

**Example**:

<pre><code>Enter L to load a game, or P to play:</code> <u>L</u>
<code>Enter the filename:</code> <u>game1.txt</u>
<code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   | o |   |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7

Enter: the column to move, q to quit, s to save
Batman enter your move:
</code></pre>

Note: This will be a menu-driven program, similar to Project 2. The user will be given a menu with choices to choose from before every move.

Note: Player 1 always goes first. As players make their moves, the squares are occupied one by one, by the 'x' and 'o' characters of the players. Player 1 is always 'x' and Player 2 is always 'o'.

## Gameplay

**If numeric is entered**

The players may choose any open position on the game board. It will place an 'x' for Player 1 and an 'o' for Player 2 at the location entered.
<pre><code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7

Enter: the column to move, q to quit, s to save
Batman enter your move:</code> <u>3</u>

<code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   |   |   |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7

Enter: the column to move, q to quit, s to save
Bane enter your move:</code></pre>

**Quit**

If 'Q' or 'q' is entered, play will stop at that point. The program will print the following:
<pre><code>Thanks for playing!</code></pre>

**Save the Board**

If 'S' or 's' is entered you will save the board to a file. The format of this save is: <pre><code>name of player 1
name of player 2
a FEN string holding all board information
</code></pre>Basically you want to printBoard to the output stream chosen -- file or monitor.
<pre><code>Enter: the column to move, q to quit, s to save
Batman enter your move:</code> <u>s</u>
<code>Enter the filename:</code> <u>game1.txt</u></pre>

Following the save, the program will print the board and the menu again and ask for the move of the **same player**.

**Illegal Moves**

Any other user input, including a position off the game board or a column that is full, will result in an error message and the player must re-enter the move. The error message is:
<pre><code>ILLEGAL MOVE: Try again</code></pre>

This means that you do **not** need to check for bad user input.

**Game Over with a Win or Draw**

Each game ends when:
* One of the players gets 4 in a row horizontally, vertically, or diagonally
* All tokens have been played and neither player wins, i.e. Draw

Output statements will be:
<pre><code>Congratulations &lt;name of winner&gt;! You won!
Draw!</code></pre>

It will also print the final board.

**Example of a Win**
<pre><code>
Congratulations Bane! You won!
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   |   |   |   |
  +---+---+---+---+---+---+---+
  | x | o | o | o | o |   |   |
  +---+---+---+---+---+---+---+
  | o | x | x | x | o | x | o |
  +---+---+---+---+---+---+---+
  | x | o | x | x | o | o | x |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7
</code></pre>

The final board will also be printed in the case of a Draw.

## Enums
Enums specify a custom primitive type. It gives a name and possible values of the type. Just like a type <code>bool</code> has possible values <code>true</code> and <code>false</code>, in this project we define a type <code>Result</code> that has possible values <code>IllegalMove</code>, <code>Draw</code>, <code>Win</code>, and <code>NoResult</code>. Here, <code>NoResult</code> means that the move was legal and there was no win or draw. We also define an enum <code>PieceType</code> that has possible values <code>Empty</code>, <code>Player1</code>, and <code>Player2</code>.

## const
When <code>const</code> is written at the end of a member function header line, that means the function cannot modify the values of the private member variables of the class.

## FEN Strings
The position notation used to describe the Connect 4 Board is based on the FEN notation used in chess. Forsyth-Edwards Notation (FEN) is a standard notation for describing a particular board position of a chess game. The purpose of FEN is to provide all the necessary information to restart a game from a particular position.

The format first lists piece placement.
* The rows are described from bottom row to top row, separated by forward slashes <code>/</code>
* Each column within a row is described from left column to right column, in the following format:
  * If a location is occupied, it will be denoted using the 'x' or 'o' character that occupies the location.
  * Unoccupied locations are noted by the number of consecutive blank locations in that row.
* After all rows of the board are written in this way, there is a space and the character of the next player to move (either 'x' or 'o').

**Examples**

FEN string for an empty board: <code>7/7/7/7/7/7 x</code>

<pre><code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   |   |   |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7
</code></pre>
FEN string for above board: <code>2x4/7/7/7/7/7 o</code>

To read this: The first row has "2x4" which is read as 2 spaces, then a 'x' token, then four spaces in that row.

<pre><code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   | o | o |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7
</code></pre>
FEN string for above board: <code>2x1oo1/2x4/7/7/7/7 x</code>

To read this: The first row has "2x1oo1" which is read as 2 spaces, an 'x' token, 1 space, an 'o' token, an 'o' token, then a final space. The leading '/' means that this ends the row, and the next row begins.

## Details on: int piecesInDirection(int row, int col, int dRow, int dCol) const

Note: piecesInDirection will return how many consecutive matching tokens there are, starting in position row and col and moving in the direction defined by the change in row (dRow) and the change in column (dCol). The token at location [row][col] is NOT counted.

**Examples**

Given the board:
<pre><code>
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  | o |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  | o |   |   |   |   |   |   |
  +---+---+---+---+---+---+---+
  | o | x | x | x |   |   |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7
</code></pre>
If you write:
<pre><code>int count = piecesInDirection(0, 1, 1, 0);</code></pre>
The function will start at row 0, column 1 (where the leftmost 'x' is located) and move up one row at a time (dRow = 1 and dCol = 0) searching for matching tokens. Since the location at [1][1] is unoccupied, the function returns 0.

If you write:
<pre><code>int count = piecesInDirection(0, 1, 0, 1);</code></pre>
The function will start at row 0, column 1 (where the leftmost 'x' is located) and move to the right one column at a time (dRow = 0 and dCol = 1) searching for matching tokens. Since the location at [0][2] and [0][3] match the 'x' and [0][4] is unoccupied, the function returns 2.

If you write:
<pre><code>int count = piecesInDirection(0, 0, 1, 0);</code></pre>
The function will start at row 0, column 0 (where the lowest 'o' is located) and move up one row at a time (dRow = 1 and dCol = 0) searching for matching tokens. The function returns 2.

If you write:
<pre><code>int count = piecesInDirection(0, 2, 0, 1);</code></pre>
The function will start at row 0, column 2 (where the middle 'x' is located) and move to the right one column at a time (dRow = 0 and dCol = 1) searching for matching tokens. The function returns 1.

If you write:
<pre><code>int count = piecesInDirection(0, 2, 0, -1);</code></pre>
The function will start at row 0, column 2 (where the middle 'x' is located) and move to the left one column at a time (dRow = 0 and dCol = -1) searching for matching tokens. The function returns 1.

If you write:
<pre><code>int count = piecesInDirection(0, 3, 1, 1);</code></pre>
The function will start at row 0, column 3 (where the rightmost 'x' is located) and move diagonally up and to the right (dRow = 1 and dCol = 1) searching for matching tokens. The function returns 0.

<code>piecesInDirection</code> will work even for a row and column that is unoccupied. However, when you call this function as part of the logic for determining a Win, you should only call it on rows and columns that are occupied by a player token.

## Grading Rubric

Here is the [grading rubric](Grading#core) for the core.

## Sample Runs

[Sample Run 1](https://github.com/eecs183/Connect4/blob/master/Sample_Run_1.txt)

[Sample Run 2](https://github.com/eecs183/Connect4/blob/master/Sample_Run_2.txt)

[Sample Run 3](https://github.com/eecs183/Connect4/blob/master/Sample_Run_3.txt)