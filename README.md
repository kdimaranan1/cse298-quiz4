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

## Question 3

List out the cells that represent the shortest path you found above. Then list the commands that would need to be sent to the robot to follow this path. The robot in question moves perfectly without any error, and reponds to two commands: it can either move forward a specified number of cells with `move(cells)`, or it can turn with `turn(radians)`. The robot should end at the goal the same direction at which it faced originally.
