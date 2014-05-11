User Manual
Program:  testGrid.cpp

This is a game where you are jumping pegs over other pegs.  Each time you jump a peg it will be removed from the board.  Your goal it to end with one peg.

Pegs are represented by a X.  You may jump a peg horizontally, vertically, or diagonally.  There must be a peg in the square you jump from, and the square you jump over.  There must not be a peg in the square you jump to.  You must only jump one square at a time.  Enter the starting square followed by the ending square, case insensitive. 

Example: a1 a3 
Example: a1 C3 
Example: D2 B2 
Enter "quit" to exit 



There is a graphical version of the game called testGridGui.cpp.  The rules of the game are the same.  Pegs are represented by circles.  You  play by clicking on the from peg, and then on the to spot.


System Manual
This program is a simple peg jumping game.  It uses a Grid class to represent the grid as a 2 dimensional vector of ints.  1 repesents a peg in a square, and 0 represents nothing.  The ints could be bools.

The Grid class has two overloaded operators.  The [] operator will return a vector of a single row.  Since vectors have the [] this means we can access the  location at row 2 column 3 with grid[2][3].

The << operator is also overloaded, and it will output the full board in a formatted way with column and row markers.

There are a few methods that aren't trivial.  applyMove will take 4 ints, and remove the peg at the start and middle locations, and then add a peg at the end.  It first checks to see if the move is legal before doing it.  To check if the move is legal it uses isLegalMove, which takes the same 4 ints, and simply returns true or false depending on if the move is legal.

areMoreMoves will check to see if there are more legal moves.  It does this by working through every square, and checking to see if jumping from each of the 8 surrounding squares across the middle square would be legal.  It returns true or false.

isGameWon will check to see if the player won the game.  It does that by just counting the pegs, and returning true if num = 1.


In the graphical version of the game, the only major differences is that output is handled by drawGrid, which displays 'o' where pegs are.  It uses a X_SHIFT and Y_SHIFT constant set at the top of the header file, which works well to shift the grid to the top of the screen on my computer, but may need to be adjusted.

There is also a new getMove method that will determine the user's move from a mouse click.  The four integers that represent the two moves are passed by reference, and modified directly by the method.
Test Logs
Square Pegs by Stephen Wetzel. 

Pegs are represented by a X
You may jump a peg horizontally, vertically, or diagonally. 
There must be a peg in the square you jump from, and the square you jump over. 
There must not be a peg in the square you jump to. 
You must only jump one square at a time. 
Enter the starting square followed by the ending square, case insensitive. 
Example: a1 a3 
Example: a1 C3 
Example: D2 B2 
Enter "quit" to exit 


Enter grid size: 3 

    1 2 3 
  +-------+ 
A |   X X | 
B | X X X | 
C | X X X | 
  +-------+ 

Enter a move: ("quit" to exit) c3 a1 

    1 2 3 
  +-------+ 
A | X X X | 
B | X   X | 
C | X X   | 
  +-------+ 

Enter a move: ("quit" to exit) a3 c3 

    1 2 3 
  +-------+ 
A | X X   | 
B | X     | 
C | X X X | 
  +-------+ 

Enter a move: ("quit" to exit) a1 a3 

    1 2 3 
  +-------+ 
A |     X | 
B | X     | 
C | X X X | 
  +-------+ 
 
Enter a move: ("quit" to exit) c1 a1 

    1 2 3 
  +-------+ 
A | X   X | 
B |       | 
C |   X X | 
  +-------+ 

Enter a move: ("quit" to exit) c3 c1 

    1 2 3 
  +-------+ 
A | X   X | 
B |       | 
C | X     | 
  +-------+ 


Game over 
