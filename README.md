Download Link: https://assignmentchef.com/product/solved-comp1020-assignment2-multi-dimensional-arrays-and-i-o
<br>
In this assignment, you will write a set of interrelated classes that will support the implementation of the board game known as Reversi or Othello. It has a fairly simple set of rules, but they won’t be described here. Instead, look at <strong>Section 3 (Rules)</strong> at <u>https://en.wikipedia.org/wiki/Reversi</u> . (<strong>You can ignore the descriptions of time clocks, transcripts, row and column labels, and other items not part of the basic rules.</strong>) There are plenty of implementations of this game, and you can play against other people online, if you’d like to try it. Here is a short video of how to play reversi (<u>https://www.youtube.com/watch?v=Ol3Id7xYsY4</u>) and a link to practice this game (<u>https://cardgames.io/reversi/</u>).

Keep all of your methods short and simple. In a properly-written object-oriented program, the work is distributed among many small methods, which call each other. Make sure to call methods already created when appropriate, instead of duplicating code for no reason. Unless specified otherwise, all instance variables must be <strong>private</strong>, and all methods should be <strong>public</strong>.  Also, unless specified otherwise, there should be <strong><em>no </em>println</strong> statements in your classes. Objects usually do not print anything, they only return <strong>String</strong> values from methods.

<h1>Phase 1: A set of related classes</h1>

In this phase, you will create a set of four classes of objects that will represent individual moves in a Reversi game. Since a move must always “flip” some of the opponent’s pieces in up to 8 different directions, some classes to represent these directions will also be useful.

The <strong>Direction</strong> class:

An object of type <strong>Direction</strong> will hold two <strong>int</strong> values to represent one of the 8 possible vertical, horizontal, or diagonal directions on a game board, as shown below. (This is not only useful for Reversi, but could be used in many other games, too.) The two integers give the change to the row index, and to the column index, that would move from one square to the next in the indicated direction. These numbers will always be -1, 0, or +1. The two numbers should not both be 0 (since that wouldn’t change any index at all), but the other 8 possible combinations are valid.

<strong> </strong>

Implement the following things in your <strong>Direction</strong> class:

<ul>

 <li>Two instance variables (private, as usual) to hold the two integer values (the row change and the column change).</li>

 <li>A constructor with two integer parameters to initialize the two instance variables. Put the row first, and the column second.</li>

 <li>Two accessors to allow your other classes to obtain these two integer values. Do not supply mutators. The integers are never supposed to change after one of these objects is created.</li>

 <li>The usual <strong>toString()</strong> It should return a <strong>String</strong> containing words, not integers. Use the words “up”, “down”, “left”, and “right” instead of -1 and +1. Use either one word, or two words, whichever is appropriate, and surround the words with “angle brackets” (&lt; &gt;). For example,</li>

</ul>

<strong>new Direction(-1,1).toString()</strong>   should give   <strong>“&lt;up right&gt;”</strong> <strong>new Direction(1,-1).toString()</strong>   should give   <strong>“&lt;down left&gt;”</strong> <strong>new Direction(1,0).toString()</strong>   should give   <strong>“&lt;down&gt;”</strong> <strong>new Direction(0,-1).toString()</strong>   should give   <strong>“&lt;left&gt;”</strong> The <strong>DirectionList</strong> class:

An object of type <strong>DirectionList</strong> will hold a list of <strong>Direction</strong>s (0 to 7). You can use an array to store them. If you know how to use an <strong>ArrayList</strong> (a topic which won’t be covered until later in the course), you can use that too.

Implement the following things in your <strong>DirectionList</strong> class:

<ul>

 <li>Instance variables (private, as usual) to store the list of <strong>Direction</strong> Use Array or ArrayList.</li>

 <li>A constructor to create an empty list.</li>

 <li>A method <strong>public void addDirection(Direction d) </strong>to add a <strong>Direction</strong> to the end of the list.</li>

 <li>A method <strong>public int length()</strong> that will return the size of the list.</li>

 <li>A method <strong>public Direction getDirection(int i)</strong> which will return the element at position<strong> i</strong> in the list (positions should start from 0 as usual).</li>

 <li>A <strong>toString()</strong> method, as usual. It should list the <strong>Direction</strong>s in the list, surrounded by <strong>{ }</strong> and separated by commas. For example, <strong>{&lt;right&gt;,&lt;down right&gt;,&lt;left&gt;}</strong>. Don’t put a comma after the last one.</li>

 <li>A method <strong>public static DirectionList allDirections()</strong> which will return a list of all 8 possible directions. This will be very useful later in the assignment. Note that this is a <strong>static</strong></li>

</ul>

The <strong>Move</strong> class:

An object of type <strong>Move</strong> will hold information describing one possible move in a game of Reversi. Since a move in this game will always “flip” opponent pieces in one or more directions, a <strong>Move </strong>object will also keep track of these directions. (This class doesn’t calculate what the directions are – it doesn’t have any way to do that – it just stores them.) Implement the following things in your <strong>Move</strong> class:

<ul>

 <li>Instance variables (private, as usual) to store the coordinates of the move (a row number and a column number), and a <strong>DirectionList</strong> giving the directions in which opposing pieces will be flipped.</li>

 <li>A constructor which accepts a row number, a column number, and a <strong>DirectionList</strong>.</li>

 <li>Accessors for the row number, the column number, and the <strong>DirectionList</strong>.</li>

 <li>A <strong>toString()</strong> method which returns a String in the following format:</li>

</ul>

<strong>(2,5) flips directions {&lt;left&gt;,&lt;down left&gt;} </strong>The <strong>MoveList</strong> class:

An object of type <strong>MoveList</strong> will hold a list of 0 or more <strong>Move</strong>s.

Implement the following things in your <strong>MoveList</strong> class:

<ul>

 <li>Instance variable(s) (private, as usual) to store the list of moves. If you use an array, give it a maximum capacity of 32 moves.</li>

 <li>A constructor to create an empty list of moves.</li>

 <li>A method <strong>public void addMove(Move m)</strong> to add a <strong>Move</strong> to the list.</li>

 <li>A <strong>toString()</strong> method which will return a multi-line <strong>String</strong> using <strong>‘
’</strong> characters to separate the moves, so that if the <strong>String</strong> were printed it would look like this:</li>

</ul>

<strong>(1,2) flips directions {&lt;down&gt;} </strong>

<strong>(2,0) flips directions {&lt;right&gt;,&lt;down right&gt;} </strong>

<strong>(2,5) flips directions {&lt;left&gt;,&lt;down left&gt;} </strong>

<strong>(4,0) flips directions {&lt;right&gt;}</strong>

<ul>

 <li>A method <strong>public boolean isEmpty()</strong> which returns <strong>true</strong> if the list is empty.</li>

 <li>A method <strong>public Move randomMove()</strong> which returns one of the moves in the list, <em>at random</em>. If the list is empty, it should return <strong>null</strong>. <strong>Testing </strong></li>

</ul>

There are four test classes that you can test your Direction, DirectionList, Move and MoveList classes. Make sure your classes work properly before starting the next phase as you need those classes in the next phase.




<h1>Phase 2: Board class for a Reversi (Othello) game</h1>

In this step, you will create a <strong>Board</strong> class that will handle all of the tasks needed to play a Reversi game. This includes finding valid moves, making moves, flipping pieces, detecting the end of the game, etc. But it does not contain any user interface code for actually playing the game.

Define a <strong>Board</strong> class. Objects of this type will store the current state of a Reversi board (which pieces are on the board, and where), provide relevant information about that state (e.g. what the valid moves are), and change that state (make moves and flip pieces).

Implement the following things in your <strong>Board</strong> class:

<ul>

 <li>Instance variable(s) (private) to store the board, using a <strong><em>multidimensional array</em></strong> of <strong>int</strong> The board will always be square, but it may be any size from 2×2 up. (A normal Reversi board is 8×8, but smaller boards will be convenient to test your program.)</li>

 <li>Any square on the board may be empty, or contain a black piece or a white piece. Assign three <strong>int</strong> values (0 for empty, 1 for black and 2 for white) to represent these possibilities, and define <strong>public</strong> constants <strong>EMPTY = 0</strong>, <strong>BLACK = 1</strong>, and <strong>WHITE = 2</strong>.</li>

 <li>A constructor which takes a single <strong>int</strong> parameter giving the desired size of the board, and sets up the board for the start of a game. There are always 2 black pieces and 2 white pieces in an X pattern in the centre of the board at the start of a game, as shown below (for 6×6 and 5×5 boards). If the size of the board is an even number, they should be in the exact centre. If the size of the board is an odd number, place them slightly up and to the left since they can’t go in the centre. The piece closest to the top left should be a white one.</li>

</ul>










<ul>

 <li>A <strong>toString()</strong> method, which will return a suitable representation of the board, such as the one shown below. You could use X and O for Black and White:</li>

</ul>

<strong>…OOO </strong>

<strong>..X.OO </strong>

<strong>..XXOO </strong>

<strong>..XXXX ….O. …… </strong>

<ul>

 <li>A method <strong>public static int opponentOf(int player)</strong> which will return the integer representing the other player. So <strong>opponentOf(BLACK)</strong> should give <strong>WHITE</strong>, and vice-versa.</li>

 <li>A method <strong>public static String nameOf(int player)</strong> which will return a String giving the name of that player. Simply return “Black” or “White”.</li>

 <li>A method <strong>public int getScore()</strong> which will return the score in the game, which is simply the number of black pieces on the board minus the number of white pieces. A positive number means Black is winning, and a negative number means White is winning.</li>

 <li>Now for the complicated one. Write a method <strong>public MoveList allValidMoves(int player)</strong> which will return a list of <strong><em>all</em></strong> of the valid moves that could be made by the indicated player. Remember that a <strong>Move</strong> object contains a list of all the directions in which opponent’s pieces will be flipped, so calculating all of that information is part of the job. A move is valid if 1) it is played on an empty square, and 2) it flips at least one of the opponent’s pieces. If there are no valid moves, it should return an empty list (not just <strong>null</strong>).

  <ul>

   <li>Do not write this as one big method!</li>

   <li>Use <strong>several</strong> <strong>smaller</strong> <strong>private</strong> helper to break down this task into manageable sections of code.</li>

   <li>You can do this in any way that you like. It would be sensible to make methods that focus on one particular square, or one particular direction from a square, or similar smaller tasks.</li>

  </ul></li>

 <li>Write a method <strong>public void makeMove(int player, Move theMove)</strong> which will make the given move, for the given player. This is the only method that will actually make changes to the board. It must place the new piece on the board, and flip all of the appropriate opponent pieces, in the directions indicated by <strong>theMove</strong>.</li>

</ul>

<h1>Phase 3: I/O and Exceptions</h1>

In this phase we want to save the progress has been made and save it as a text file by calling <strong>saveFile(String fileName)</strong> method. This file has a special format. The first line of the file will be the dimension of the board and the following lines represent the board setup (<strong>.</strong> for Empty, <strong>O</strong> for Black, and <strong>X</strong> for White). Here is an example




4

..o. .oo. xxxx

.o.x




As the second option to start the game, instead of creating a new regular board, you can also use a method with which you can import a specific board setup. To do this, you need to define a method, <strong>importBoardSetup(String fileName), </strong>which reads the data from a text file specified by ‘fileName’ and set the dimension as well as set the values of the 2D array representing the board. The following is an example of an input text file:







..xxx.

o.xxx. .oxox.

..o.x. ….x.







To get full mark for this section you need to define the following methods inside your Board class:

<ul>

 <li>Your Board class should have <strong>saveFile(String fileName)</strong> You need this method to save your board (as a text file).</li>

 <li>You need to write <strong>importBoardSetup(String fileName)</strong> to read a text file that represents a Board setup (set the size of the board and set the values of the 2D array representing the board). This method should be able to throw IOException if the data in not valid. Special exception message includes:</li>

 <li>“<strong><u>The number of columns and rows doesn’t match</u></strong><u>”</u></li>

 <li>“<strong><u>Unrecognized character</u></strong>”, for example if there is a character(s) other than ., x, o in the file</li>

 <li>“<strong><u>number of rows/columns less than 2</u></strong>”</li>

 <li>Make sure that you are printing the messages mentioned above for special cases.</li>

 <li>You need to define a new constructor <strong>Board(String fileName)</strong> that is going to create a new Board based on the imported Board setup by calling the <strong>importBoardSetup(String fileName)</strong> inside your constructor.</li>

</ul>




<h2>Test</h2>

You can use the supplied main program RandomOthello.java to test your Board class. This program plays games of Othello by selecting moves for Black and White at random. You can modify this program if you wish to allow human players to pick moves, but that is not required. (Don’t hand in this program.)

<strong> </strong>