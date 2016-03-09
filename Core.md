The goal of the Core is to implement a fully-functioning game of Connect 4. The game will be played in the terminal window with two players manually entering their moves. The program will check for a win or draw after every move. Below we will outline the game, the functions involved in the implementation, and a few sample runs of the fully-implemented program.

The files included in this project are listed below.
* **board.h**: Declarations of global constant variables and enums used throughout the project. Enums are explained below. Declarations for the Board class.
* **board.cpp**: Definitions of Board member functions.
* **connect4.h**: Declarations of functions to read a board from a file and to write a board to a file.
* **connect4.cpp**: Definitions of the functions in connect4.h and the main function.
* **graphics.h**: Declarations of functions needed for graphics. Only used for optional graphics Reach.
* **graphics.cpp**: Definitions of functions needed for graphics functionality. Only used for optional graphics Reach.

**How to Play Connect 4**  
Connect 4 is a two-player game which takes place on a 6 x 7 rectangular board. Play 1 has 21 'x' tokens and Player 2 has 21 'o' tokens. Each player can drop a token at the top of the board in one of the seven columns; the token falls down and fills the lowest unoccupied square. A player cannot drop a token in a column if it is already full (i.e. it already contains six tokens).

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

**Specifications**

The game begins by asking if you wish to load a game or to play a game. Note: this entry is not case-sensitive. An uppercase P or a lowercase p will both choose "play".

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
name of player 1
name of player 2
a FEN string holding all board information

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

**Play**

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

**Illegal Moves**

A position off the game board or a column that is full will result in an error message and the player must re-enter the move. The error message is:
<pre><code>ILLEGAL MOVE: Try again</code></pre>

**Quit**

If 'q' is entered, play will stop at that point. The program will print the following:
<pre><code>Thanks for playing!</code></pre>

**Save the Board**

if 's' is entered you will save the board to a file. The format of this save is FEN strings. Basically you want to printBoard to the output stream chosen -- file or monitor.
<pre><code>Enter: the column to move, q to quit, s to save
Batman enter your move:</code> <u>s</u>
<code>Enter the filename:</code> <u>game1.txt</u></pre>

Following the save, the program will print the board again and ask for the move of the **same player**.

**Game Over with a Win or Draw**

Each game ends when:
* One of the players gets 4 in a row horizontally, vertically, or diagonally
*;or
* All tokens have been played and neither player wins, i.e. Draw

Output statements will be:
<pre><code>Congratulations <name of winner>! You won!
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

The final board will also be printed in the case of a Draw.

**Enums**

Enums specify a custom primitive type. It gives a name and possible values of the type. Just like a type <pre><code>bool</code></pre> has possible values <pre><code>true</code></pre> and <pre><code>false</code></pre>, in this project we define a type <pre><code>Result</code></pre> that has possible values <pre><code>IllegalMove</code></pre>, <codeDraw</code></pre>, <pre><code>Win</code></pre>, and <pre><code>NoResult</code></pre>. We also define an enum <pre><code>PieceType</code></pre> that has possible values <pre><code>Empty</code></pre>, <pre><code>Player1</code></pre>, and <pre><code>Player2</code></pre>.

**FEN Strings**

The position notation used to describe the Connect 4 Board is based on the FEN notation used in chess. Forsyth-Edwards Notation (FEN) is a standard notation for describing a particular board position of a chess game. The purpose of FEN is to provide all the necessary information to restart a game from a particular position.

The format first lists piece placement. Each row is described from row 1 to row 6 (bottom row to top row); each column within a row is described from column 1 to column 7 (left column to right column). Note: these numbers are according to the display and NOT by indices of the array. 
* If a location is occupied, it will be denoted using the 'x' or 'o' character that occupies the location.
* Unoccupied locations are noted by the number of consecutive blank locations. 
* A single unoccupied location is denoted as '1'. Each row will be separated by a single '/'.

**Examples**

FEN string for an empty board: <pre><code>7/7/7/7/7/7 x</code></pre>

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
FEN string for above board: <pre><code>2x4/7/7/7/7/7/7 o</code>

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
  |   |   | x |   |   |   |   |
  +---+---+---+---+---+---+---+
  |   |   | x |   | o | o |   |
  +---+---+---+---+---+---+---+
col 1   2   3   4   5   6   7
</code></pre>
FEN string for above board: <pre><code>2x1oo1/2x4/7/7/7/7/7 x</code></pre>

**Details on: int piecesInDirection(int row, int col, int dRow, int dCol) const**

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