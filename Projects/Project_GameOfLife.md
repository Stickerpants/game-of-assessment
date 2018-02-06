# Introduction

Conway's Game of Life is a simple simulation that can be made in any programming language. Conceptually, the idea is easy to understand: imagine a flat world, that's divided into a grid. Each square of the grid is called a cell. Each cell can either be on or off. Sometimes, people like to call these states "alive" and "dead". Time progresses in the world based on an interval, called a tick.

Every tick, cells will evolve based on four basic rules. When we talk about the neighbors of a cell, we refer to the 8 cells that surround it. Below is a diagram. Keep in mind that the cell itself isn't counted - only its neighbors.

```
* = Neighbor

* * *
* @ *
* * *
```

1. If an alive cell has less than 2 alive neighbors, then it dies (turns off), because it is lonely.
2. If an alive cell has more than 3 alive neighbors, then it also dies, because it is too crowded.
3. If an alive cell has 2 or 3 alive neighbors, then it continues living since it is happy.
4. If a dead cell has exactly 3 alive neighbors, then it becomes alive (turns on), like it is born.

Something important to keep in mind, is there are two stages to how the tick happens. First, every cell looks at the current state the world is in, and figures out what they need to do (based on the rules above). A cell could do one of three things: it could die (Rules 1 and 2), it could stay as it is (Rule 3, or if no rule applies), or it could come alive (Rule 4). After the cells have figured out what to do, the second stage happens, where they make their change. The reason why this is done in two stages is to prevent a tricky condition: If cells immediately changed, then the cells around it might end up making a different choice, and we want to avoid that.

In other words, cells always make their decision on what to do based on what the world was like at that tick, and never based on "in-between" information.

To demonstrate the Game of Life more concretely, here's a pattern that repeats itself infinitely. People like to call this pattern the "blinker".

```
# = Off
* = On

# * #
# * #
# * #
```

Initial state of the world. We have three live cells (in a vertical line), and 6 dead cells.

```
# # #
* * *
# # #
```

First tick happens. The center cell stays alive, since it has 2 neighbors (Rule 3). The center-top cell dies, since it only has one neighbor (Rule 1). The same thing happens to the center-bottom cell. The center-left cell comes to life, since it has exactly 3 neighbors (Rule 4). The same thing happens to the center-right cell.

```
# * #
# * #
# * #
```

Second tick happens. The center cell stays alive again, since it still has 2 neighbors. The center-left and center-right cells die, since they only have one neighbor. The center-top and center-bottom cells come to life, since they have exactly 3 neighbors.

From here, the pattern continues to alternate between the two states (vertical bar and horizontal bar).

# Objective

Implement the Game of Life, as described above. Before you start, look at the list of extensions, and decide which ones you want to attempt. Relevant extensions are tagged in the question. It's easier to plan the design of your program, if you know the full breadth of want you want to accomplish first. You may use any programming language you'd like. Keep in mind that you are **not** expected to implement every extension. Recommended is to pick 2 or 3 of them that interest you.

Searching external help resources is encouraged! It's not expected that you should be able to implement everything in this program without searching Google or Stackoverflow.

However: looking up full, complete solutions and copy-pasting code is **extremely discouraged**, as it defeats the purporse of the project. 

The program shall read the initial state of the world from a file. Assume that the octothorpe (`#`) represents a cell that is dead, and the asterisk (`*`) represents a cell that is alive.

You may assume that the grid size is determined by whatever the dimensions of the given initial world are (Extension 1). Assume that anything past the edge of the grid is always dead (Extension 2). As an example, here's the blinker specified the world file (with some extra dead cells surrounding it):

```
#####
#***#
#####
```

Note that there's no space between each symbol, to keep things more compact.

The program shall print each iteration out to the console, repeating infinitely until it's stopped.

The program shall receive the filename of the world file to load through the arguments to the program call. For example, if your program was compiled to an executable, you might use it like this:

```
./gameoflife myworld.txt
```

Think carefully about possible ways the user could break your program. What if they give you a world file that isn't formatted properly? You should handle these cases in a graceful way that lets the user know what's broken.

Make sure you build your program using clean, well written code that will be easy to modify and add to in the future. Put yourself in the mindset that this is a project that you'll want to work on over a long period of time, and that other people may be reading and adding to your code. This is the reality of any major software project!

To begin the project, fork this repository and write your solution. This keeps a nice record of everyone who is working on it.

# Extensions

## Extension 1

In the original specification of the Game of Life, the world is infinite. Implement this infinite world. Assume that the center of the world starts from the center of the initial world file.

## Extension 2

Consider different ways of handling the edges of the grid. What if the grid were to "wrap" around, and consider cells from the opposite side of the grid? Implement this "wrap-around" grid handling as an optional strategy in your program. 

Notes: 
* Not compatible with Extension 1.

## Extension 3

The Game of Life is a specific configuration of something called a "Cellular Automaton". Different rules arise in different simulations. Implement the ability for a user to specify the rules for themselves, in a file. The program should read the rule file to determine how to mutate the world. The rules shall be specified using the language below, and it's up to you to parse the language.

The language has two types of statements.

* A semicolon (`;`) denotes a comment. We ignore everything that follows a semicolon. 
* `CELL (ALIVE/DEAD) -> (ALIVE/DEAD) IF N IS [(LESS THAN/GREATER THAN) [OR EQUAL TO]] <integer>)`
	* This is a cell directive. The first part describes what state applies to the cell. `ALIVE -> DEAD` means we should apply this rule to cells that are alive, and kill it if the condition holds.
	* The second part is the condition, which performs a test on a number of neighbors. We can test for strict inequality using `LESS THAN` or `GREATER THAN`, or the similar `LESS THAN OR EQUAL TO`. We can also test for exact matches using `IS`.

Here's the Game of Life rule-set written in the language.

```
; These are the rules for the Game of Life.
CELL ALIVE -> DEAD IF N IS LESS THAN 2
CELL ALIVE -> DEAD IF N IS GREATER THAN 3
CELL DEAD -> ALIVE IF N IS 3
```

## Extension 4

The Game of Life would be a lot more interesting if it had graphics. Put a graphical interface on top of your program. How things are displayed are up to you to decide. The program must be able to switch between console output mode and graphical mode.

## Extension 5

Give the user more control over the simulation by implementing time controls. The user should be able to pause, fast-forward, rewind, and play one step forwards or backwards.

Notes:

* May be easier if done with Extension 4, since it makes writing user controls significantly easier.

## Extension 6

Make things more fun by allowing the user to modify the world to turn cells on/off. The user should only be allowed to modify the world when the game is paused (Extension 5).

Notes:

* Requires part of Extension 5 for pause control.
* May be easier if done with Extension 4, since it makes writing user controls significantly easier.

## Extension 7

In order to be more confident that your program is working, write a suite of unit tests to ensure everything in your program behaves correctly. Think about how you would go about testing your program in an automated way. Does it change the way you might structure your code?

## Extension 8

Implement a way to pan around your world, to look at different parts of it.

Notes:

* Requires Extension 1 to be interesting.
* May be easier if done with Extension 4, since it makes writing user controls significantly easier.

## Extension 9

Implement a way to zoom in and out of your world. If you do this for ASCII-based output, you will have to think about how to represent the change in scale when the size of your "unit" stays the same.

Notes:

* May be easier if done with Extension 4, since it makes writing user controls significantly easier.
