Sudoku Generator & Solver
A console Sudoku application in modern C++17. It generates a random 9x9 puzzle at a chosen difficulty, lets you play it interactively, and reveals the solution on request.
This is a rewrite, in portable standard C++, of a Sudoku project I first built during an Object-Oriented Programming course. The original used Turbo C++ specific calls; this version replaces those with standard library features so it compiles and runs on any current compiler.
Why this one is worth a look
Most Sudoku generators just remove random cells from a solved grid. That can produce a puzzle with more than one valid solution, which is not a real Sudoku. This one removes cells one at a time and, after each removal, counts how many solutions the puzzle still has. If removing a cell would allow a second solution, the cell goes back. The result is a puzzle that is guaranteed to have exactly one answer, the same standard a published Sudoku puzzle has to meet.
How it works
Generation: recursive backtracking fills an empty grid completely, trying digits 1 to 9 in a randomized order at each cell.
Digging holes: cells are removed one at a time in random order. After each removal, a solution counter checks whether the puzzle is still uniquely solvable, stopping early once it finds a second solution. If removal breaks uniqueness, the cell is restored.
Solving and validation: the same backtracking routine that fills the grid also solves it, and the same row/column/box rule validates every move a player makes.
Build and run
```bash
g++ -std=c++17 -O2 sudoku.cpp -o sudoku
./sudoku
```
Sample session
```
==== Sudoku Generator & Solver ====

Select difficulty: 1) Easy 2) Medium 3) Hard (q to quit): 2

   1 2 3   4 5 6   7 8 9
  +-------+-------+-------+
A | . 8 2 | 1 . . | 9 3 6 |
B | . 7 9 | 8 . . | 5 1 4 |
...
```
My contribution
Solo project. I designed the class structure, the backtracking generator and solver, the uniqueness-guarantee logic, and the interactive console loop, and rewrote the original Turbo C++ version into standard C++17.
Full project report (with sample screenshots): lawazislam.com/projects
