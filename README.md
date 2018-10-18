# Picross-Solver
This program uses AI to solve picross (aka nonogram) puzzles.
Picross puzzles are similar to sudoku in that every row and column has a set of rules that must be followed in order complete the puzzle.
Play a picross game here: https://www.puzzle-nonograms.com/ to try one for yourself!
This program solves these puzzles by modeling the puzzle as a constraint based problem (CSP).
The variables for the CSP are each row/column in the game. The domain for each variable is the set of all possible configurations for the particular row/column.
The constraints for the CSP are the rules for picross, every row/column configuration has to agree with every other row/column rules.

In order to solve the picross game intelligently, my algorithm lays down each row in order of decreasing constraint.
This means that the most constrained rows will be selected to be placed first.
The algorithm recursively places the next most constrained row, and continues until all rows have been placed successfully.
If any column does not have any configurations that agree with the currently placed rows, the algorithm understands that it made a mistake and either tries a new configuration for the row, or backtracks to the previous row if none of the configurations in the current row are valid.
What makes this program intelligent is that it chooses the rows with the least amount of configurations first (most constrained).
This minimizes the amount of backtracking that will occur, and can speed up the algorithm exponentially when compared to blindly selecting the order of rows.

To run the program, you must have pygame and numpy installed as packages. Issue the command,
"python3 nonogram.py problems/tests/10_10_1.npy"
Note that this program requires large amounts of memory for the bigger puzzles due to the amount of recursion that occurs during my algorithm.
For most puzzles, this algorithm finds a solution in less than a second of runtime.

To see the puzzle solutions, view the images in the folder titled "solutions".
