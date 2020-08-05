# CSE 298 - Quiz 4

Due: 8/04 by end of day

Make at least 1 commit per question.

## Question 1

What is the difference between Dijkstra's Algorithm and A*. Why would one use Dijkstra's over A* and vice versa?

Dijkstra's Algorithm is different from A* in that it doesn't take information in about the robot, which means it wouldn't be able to plan around an obstacle if it was in its path unlike A* which takes into account an occupancy grid. So if you were moving a robot and were expecting that its environment may change or that it would have obstacles in its way, you would use A* to be able to find spot these and find the shortest path while avoiding them. However, if you were simply just finding the shortest path from a starting point to an ending point, and you did not have to be aware of any obstacles, you could use Dijkstra's over A* as Dijkstra is optimal in that it will always find the absolute shortest path.

## Question 2

Consider the following robot in a grid 2D grid world:

![Gridworld](https://github.com/cmontella/cse298-quiz4/blob/master/gridworld.png?raw=true)

The cell (0,0) is at the bottom left. The robot starts at cell (3,3) and is facing in the 0 radians direction. The robot's goal cell is (12,1), facing the 0 radians direction as well.

Perform the A* algorithm by hand to find the shortest path from the robot's starting location to the goal. Write down each step of the algorithm, including the current cell, open set of cells O, the closed set of cells C, the parent of each cell, and the current g-score and f-scores for each cell (these can be a sparse lists i.e. you don't need to write the scores/parents of the cells haven't been considered by the algorithm yet). You can use any heuristic you like, but specify the one you are using.

Starting Cond.: n0 = (3,3) ng = (12, 1) h(c,t) = [(cx -tx)^2 + (cy - ty)^2]^(1/2)
	0 = {(3,3)}
	C = 0
Pass 1: nC = (3,3)
	O = {(4, 3), (4, 2), (5, 1), (6, 1), (7,1), (8, 1), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3)}
	P = {(4,3), (4, 2), (4,4), (3, 2,), (3,4), (3,2), (2, 2), (2, 3), (2,4)}
	g-score= .5 + .5 (diagonal, so .5) = 1
	f-score= 1 + [(4 - 12)^2 + (2 - 1)^2]^(1/2) = 9.06
Pass 2: nC = (4, 2)
	O = {(4, 3), (5, 1), (6, 1), (7,1), (8, 1), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2)}
	P = {(3,3), (4, 3), (5,3), (5, 2), (4,1), (3,2), (6,1),(3,1)}
	g-score= .5 + 1 = 1.5
	f-score = 1.5 + [(5 - 12)^2 + (1 - 1)^2]^(1/2) = 8.5
Pass 3: nC = (5,1)
	0 = {(4, 3), (6, 1), (7,1), (8, 1), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1)}
	P = {(6,1), (6,2), (6,0), (5,2), (5,0), (4,1), (4,0), (4,2)}
	g-score = 1 + 2 = 3
	f-score = 3 + [(6 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 4: nC = (6,1)
	0 = {(4, 3), (7,1), (8, 1), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1)}
	P = {(7,1), (7,2), (7,0), (6,2), (6,0), (5,0), (5,1), (5,2)}
	g-score = 1 + 3 = 4
	f-score = 4 + [(7 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 5: nC = (7,1)
	0 = {(4, 3), (8, 1), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1)}
	P = {(8,1), (8,2), (8,0), (7,2), (7,0), (6,0), (6,1), (6,2)}
	g-score = 1 + 4 = 5
	f-score = 5 + [(8 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 6: nC = (8,1)
	0 = {(4, 3), (9, 1), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1), (8,1)}
	P = {(8,2), (8,0), (7,2), (7,0), (9,0), (7,1), (9,2), (9,1)}
	g-score = 1 + 5 = 6
	f-score = 6 + [(9 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 7: nC = (9,1)
	0 = {(4, 3), (10, 1), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1), (8,1), (9, 1)}
	P = {(9,2), (9,0), (8,2), (8,0), (10,0), (8,1), (10,2), (10,1)}
	g-score = 1 + 6 = 7
	f-score = 7 + [(10 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 8: nC = (10,1)
	0 = {(4, 3), (11,1), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1), (8,1), (9, 1), (10,1)}
	P = {(10,2), (10,0), (9,2), (9,0), (11,0), (9,1), (11,2), (11,1)}
	g-score = 1 + 7 = 8
	f-score = 8 + [(11 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 9: nC = (11,1)
	0 = {(4, 3), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2), (12, 1)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1), (8,1), (9, 1), (10,1), (11,1)}
	P = {(11,2), (11,0), (10,2), (10,0), (12,0), (10,1), (12,2), (12,1)}
	g-score = 1 + 8 = 9
	f-score = 9 + [(12 - 12)^2 + (1 - 1)^2]^(1/2) = 9
Pass 10: nC = (12,1) ==> stop condition
	0 = {(4, 3), (5,3), (6,3), (7, 3), (8, 3), (9, 3), (10, 3), (11, 2)}
	C = {(3,3), (4,2), (5,1), (6,1), (7,1), (8,1), (9, 1), (10,1), (11,1), (12, 1)}

## Question 3

List out the cells that represent the shortest path you found above. Then list the commands that would need to be sent to the robot to follow this path. The robot in question moves perfectly without any error, and reponds to two commands: it can either move forward a specified number of cells with `move(cells)`, or it can turn with `turn(radians)`. The robot should end at the goal the same direction at which it faced originally.

Path: (4,2), (5,1), (6,1), (7,1), (8,1), (9, 1), (10,1), (11,1), (12, 1)
Commands: Pass 1: turn(-pi/4) & move(1)
	Pass 2: move(1)
	Pass 3: turn(pi/4) & move(1)
	Pass 4: move(1)
	Pass 5: move(1)
	Pass 6: move(1)
	Pass 7: move(1)
	Pass 8: move(1)
	Pass 9: move(1)
	Pass 10: move(1)