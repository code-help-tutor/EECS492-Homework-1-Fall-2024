# EECS492 Homework 1 Fall 2024

## EECS 492 - Homework 1 (Fall 2024)

**Due**: September 27, 2024 at 11:59pm

**September 17, 2024**

### Logistics

#### Submission Guidelines

**IMPORTANT NOTE**: It is essential that you read carefully the policies in the Syllabus section on Homework. It discusses what counts as late and how late penalties will be applied. Please also be sure you have read and understand the Academic Integrity section, including the sections on collaboration and the use of generative AI. The Generative AI section also includes a link to an example citation and explanation. You will be held responsible for following these policies, with violations being reported to the Honor Council.

The due date for this assignment is September 27, 2024 at 11:59pm. The submission is tracked using Gradescope. The written section and programming section are graded and penalized separately. Also note that any change you make to the homework already submitted on Gradescope counts as a resubmission.

You must submit the following files to Gradescope (note that there are two separate Gradescope submissions):
1. A legible PDF containing the solutions to the written section. You can write your solutions by hand, use a tablet, or typeset your solutions in LATEX. We only ask that you make it easy to read and not too verbose so that graders don’t struggle to understand your writing. You must submit the written section to the Gradescope individually.
2. The completed `Agent.py` file to the programming section.

#### Grading Policy

Regrade requests must be submitted to Gradescope within one week of when the grades for the item are made available. Later regrade requests will not be accepted. We will provide solutions, along with the exact grading rubric used.

### 1 Written [50 Points]

#### 1.1 Designing Agents [5.5 Points]

Tic - tac - toe is a game for two players who take turns marking the spaces in a three - by - three grid with X or O. The game’s objective is to be the first in placing three of their markers in a horizontal, vertical, or diagonal row (see Figure 1).

**Figure 1**: A game of Tic - Tac - Toe where the O player has won, as it has three markers in a diagonal row.

You are now tasked with developing an AI algorithm for a tic - tac - toe agent. The agent is a robot that can play against another agent (human or robot) on a piece of paper using a pen. The agent must be capable of:
• detecting whether a marker is a X or O
• drawing a marker in one of the nine grids
• detecting the empty grids and markers already present on the paper
• using this information to determine if it has won, lost, or tied the game

Note that the agent is not just playing one time, but rather, is a robot that is supposed to be able to play multiple games as many times as needed. Now, answer the following questions - note that some of these cases might be ambiguous, so justify your answers and explicitly state any assumptions

(a) Create the PEAS description for the task environment, where the task environment includes all the games the agent plays.
(b) Identify the characteristics of the environment and provide a brief justification as to why you characterized the environment in that way

As a reminder, the characteristics of the environments are as follows:
• Fully observable vs. partially observable
• Single - agent vs. multi - agent
• Deterministic vs. nondeterministic
• Episodic vs. sequential
• Static vs. dynamic
• Discrete vs. continuous
• Known vs. unknown

#### 1.2 Hands - On Search [18 Points]

Consider the search tree shown in Figure 2, including nodes A through K. The state of node A is our initial state (shown in orange). Nodes G and J share the same state and are valid goals (shown in blue). The label by an edge is the cost associated with the path between the edge’s vertices.

Assume that when a node is expanded, its children are added to the frontier in an order such that when the nodes are popped, they are visited from the left to the right. That is, for breadth - first search, the child from the leftmost branch is added in the first. For depth - first search, the child from the rightmost branch is added in the first (See Figure 3.11 in the R & N textbook).

For frontiers that use a priority queue, nodes with the same priority (path - cost, heuristic value, or the sum of path - cost and heuristic value) will be popped in alphabetical order. For instance, if node B and node C have the same priority, node B is popped first, followed by node C.

**Figure 2**: The Search Tree, with Path Costs

| ℎ() |
| ---- |
| A 3 |
| B 4 |
| C 7 |
| D 5 |
| E 15 |
| F 14 |
| G 0 |
| H 1 |
| I 6 |
| J 0 |
| K 8 |

**Figure 3**: Heuristic Values for the States

An admissible heuristic function is provided to you in Figure 3, which gives the value of the heuristic function for each node’s state. For the following search methods, list the order in which nodes were expanded from the frontier (i.e., all nodes that you called `EXPAND(node)` on as seen in the pseudocode in lectures) from the start till the goal is reached. Please show your work for partial credits.

(a) Breadth - First Search
(b) Depth - First Search. Goal test after popping from the frontier and before calling `Ex - pand(node)`.
(c) Iterative Deepening. See updated lecture slides for precise pseudocode.
(d) Uniform Cost Search
(e) Greedy Best - First Search using the heuristic function provided
(f) A - Star Search using the heuristic function provided

#### 1.3 Brick Sorting Machine [8 Points]

A brick factory produces different styles of brick, which they want to ship out in a single batch of crates, each containing only one type of brick; right now, however, each crate is loaded randomly. The factory just installed a robot arm mounted on a linear track over the crate storage area which they want to use to sort the crates. The crates are all laid out in a line, and the arm can take three actions:
1. move itself left or right by one crate,
2. grab a brick of a specific type from the crate below it, or
3. place the brick it’s holding onto the crate below it.

Note that the arm can only hold one brick at a time!

Your job is to design a search algorithm which will find the shortest sequence of actions which will result in each crate containing only one kind of brick. Thankfully, you know the initial contents of each crate ahead of time. Provide clear and detailed descriptions for each of the elements below. You don’t need to provide implementation details unless you want to (e.g., you don’t need to say “I would use a hashmap for ”), but your descriptions should include enough detail that it’s clear you considered how the algorithm might be implemented.

(a) State space: The discrete pieces of information which define the state space. In other words, when considering a particular state, what are all the things you need to know?
(b) Actions: How each of the three actions generates a successor state from an explored state, in terms of your state representation.
(c) Goal test: What must be true for a state to be a goal state, in terms of your state representation.
(d) Search algorithm: Which (non - heuristic) search algorithm is optimal for this task, and the data structure which defines its frontier. Justify your choice. Consider both space and time complexity. Hint: think about the structure of your state space and whether a reached set would be beneficial or not.

#### 1.4 Heuristics [9 Points]

(a) A knight is a chess piece that moves in an ’L’ shape. One knight move is two squares vertically and one square horizontally, or two squares horizontally and one square vertically. Each knight move costs 1. You are given a chessboard with a start square and an end square, and your task is to find the minimum number of knight moves needed for a knight to get from the start square to the end square. Explain why Manhattan distance would not be a consistent heuristic for A - Star here, and develop your own consistent heuristic. Please justify why your proposed heuristic is consistent.

**Figure 4**: Valid Knight moves, indicated by the small black squares

(b) Consider a grid world with a single goal, where the allowed moves are LEFT, RIGHT, UP, and DOWN (you are unable to move diagonally). The cost of each move LEFT, RIGHT, UP and DOWN is 1. Let `h1(s)` be the Manhattan distance from state `s` to the goal, and let `h2(s)` be the Euclidean distance from `s` to the goal. You also have the following function `h3`:

Function `h3()`: 
```
← a random number from 1 to 10, inclusive of both;
if ≤ 3 then
    return `h1(s)`;
end
return `h2(s)`;
```

Is `h3` a consistent heuristic? Justify your answer.

#### 1.5 Hill Climbing [9.5 Points]

Your friend guards each of their files with a 2 - digit PIN code, but since they keep forgetting it, they decide to implement an AI agent that uses hill climbing to find it automatically. Each PIN comprises two integers, `i1` and `i2`, each of which can take values from 0 to 9. They implement the following agent - the agent automatically submits a candidate PIN, and if it’s correct, the file unlocks. If the guessed PIN is incorrect, the agent receives a score that measures how good the guess was. If the two digits entered are `i1` and `i2`, then the score returned is `h(i1, i2) = 11 + |i1 - 1| + 11 + |i2 - 2|`

The agent then uses a hill - climbing algorithm to attempt to find the PIN. The algorithm generates neighbors by creating all guesses that are different by one digit. In other words, if the current state is `(i1, i2)`, the neighbors generated are `(i1 - 1, i2)`, `(i1 + 1, i2)`, `(i1, i2 - 1)`, and `(i1, i2 + 1)`. The algorithm doesn’t generate any states outside the valid (0,0) to (9,9) range. In the event of a tie in the `h` value, the state with the lowest value is selected.

(a) Assume that the initial guess for the PIN is (5,5) and that the actual PIN is (1,2). List the steps taken by the hill - climbing algorithm till it terminates. If it does not, explain why.
(b) Is this algorithm guaranteed to find the correct PIN code? Explain your answer. Feel free to use a graphing tool like GeoGebra to help you solve this.
(c) Now assume that the algorithm is hard - coded to terminate after `n` steps. Does your answer to part (b) change if
(i) `n = 10`
(ii) `n = 20`
(d) Suppose we modify the heuristic a bit so that it’s now: `h(i1, i2) = |11 + (i1 - 1) + 11 + (i2 - 2)|`
Is this version of hill - climbing search guaranteed to find a solution? Explain your answer.

### 2 Programming [50 Points]

#### 2.1 Setup

All programming assignments for this course use Python. If you’re new to Python or not very experienced with it, please come to office hours; we’re happy to help! We recommend also checking out the Python section in the Resources document on Google Drive. We have also shared a document Debugging Tips to help you debug your code.

We highly recommend creating a new virtual environment for the assignment under the Cod - ing folder. You can then simply install the requirements by running the command `python -m pip install -r requirements.txt`

#### 2.2 Problem Statement

In this programming section, you’ll be coding an agent that searches a maze. More specifically, you’ll be implementing the following search algorithms (graph search) -
• BFS (NOT best - first - search with FIFO queue)
• DFS
• UCS
• A - Star

Unlike lectures and previous examples, these mazes may (or may not) have multiple goals. As such, we’ll be modifying our heuristic to be the Euclidean distance to the closest goal.

Complete the `Agent.py` file and submit it to Gradescope. You will be evaluated using the Autograder on 10 test mazes on every algorithm. In `Agent.py`, you must complete the following functions
i. `heuristic_function`: returning the minimum Euclidean (straight line) distance between the AStar Node’s coordinate and the end coordinates
ii. the three comparator functions for A - star nodes `__eq__`, `__lt__`, `__gt__`
iii. `goal_test`
iv. `expand_node`
v. `bfs`
vi. `dfs`
vii. `ucs`
viii. `astar`

For simplicity, please add nodes to the frontier directly instead of updating an existing node.

Please go through `Maze.py` and `Agent.py` before you begin! The files are annotated with `TODO` in every location where you need to add code and have multiple comments, tips, and recommendations for how to proceed. `util.py` is there to help with type checking in IDEs, please feel free to ignore it. In addition, you will never need to modify `maze.py` or `util.py`.

#### Maze structure

Each test case is a text file (saved as a `.test` file, but you can open it in any text editor). Here’s what Test case 1 looks like:

```
3 3
1 1 1 1
...
A∗B
...
```

The first line of input lists the width (`w`), and the height (`h`) of the maze.
The second input line lists the cost of going left, right, up, and down correspondingly. The next three lines delineate the elements in the grid. ‘A’ denotes the starting point of the agent. ‘B’ denotes a goal state. ‘.’ denotes a spot where the agent can freely land, while ‘*’ denotes a wall.

#### 2.3 Testing locally

We’ve provided four test cases that you can use to test your implementation. You can run it with `python LocalTest.py {TESTNUMBER} {SEARCH ALGORITHM}`.

That being said, we have not provided solutions for them. The `LocalTest.py` file will show you what the maze looks like and the path your agent found. You can solve the maze and determine if your algorithm works correctly.

Test cases 1,2 and 3 are identical on Gradescope. There are no hidden test cases - your score on Gradescope is the score you can expect to receive for this section.

An example of what you should see after running `LocalTest.py` for Test1 on BFS and DFS can be seen in Figure 5. The red dot is the start position, the yellow star is the goal, and the green arrows indicate the path found by the algorithm. The grey cells indicate walls, while the cells are shaded based on how early on into the algorithm’s execution they are expanded. The darker the shade of blue, the earlier it was expanded. White cells have not been expanded.

**(a) BFS**
**(b) DFS**

**Figure 5**: Expected paths found by BFS and DFS on test case 1# EECS492 Homework 1 Fall 2024

# CS Tutor | 计算机编程辅导 | Code Help | Programming Help

# WeChat: cstutorcs

# Email: tutorcs@163.com

# QQ: 749389476

# 非中介, 直接联系程序员本人
