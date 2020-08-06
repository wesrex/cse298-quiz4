# CSE 298 - Quiz 4

Due: 8/04 by end of day

Make at least 1 commit per question.

## Question 1

What is the difference between Dijkstra's Algorithm and A*. Why would one use Dijkstra's over A* and vice versa?
-Dijktras is good for simpler problems, if you need to simply choose the fastest route with no other factors to consider other than time taken on the road, dijkstras is the better choice.  A* on the other hand is heuristic meaning that it takes into account rules you set in place, like preferring to pick routes that are on the way to the destination first. ie. if you are mapping out a route to your office with dijkstras and there is normally a faster route (A) but because there is traffic today each of the roads along (A) increase their cost and thus could send you on a different route (B) with no traffic but takes you away from your office at first increasing time, A* would know you want to always head in the general direction of your office and pick route A (As long as traffic doesn't make the cost exuberantly High).

## Question 2

Consider the following robot in a grid 2D grid world:

![Gridworld](https://github.com/cmontella/cse298-quiz4/blob/master/gridworld.png?raw=true)

The cell (0,0) is at the bottom left. The robot starts at cell (3,3) and is facing in the 0 radians direction. The robot's goal cell is (12,1), facing the 0 radians direction as well.

Perform the A* algorithm by hand to find the shortest path from the robot's starting location to the goal. Write down each step of the algorithm, including the current cell, open set of cells O, the closed set of cells C, the parent of each cell, and the current g-score and f-scores for each cell (these can be a sparse lists i.e. you don't need to write the scores/parents of the cells haven't been considered by the algorithm yet). You can use any heuristic you like, but specify the one you are using.

-F = goal score
G  = next cell score
Using the heuristic of general distance to the goal, formulaically that would be sqrt((cx - tx)^2 + (cy - ty)^2) where c = current gird space and t = target grid space. you start with no closed cells and at each step check to make sure that you arent at the goal (if you are than terminate).  Next add (3,3) to closed as that's where we start and check all neighbors finding the shortest g and f score and using the shortest first, thus moving us to (4,3) and adding to closed assigning the parent node (3,3) the f score and g score, if there ever is a shorter distance to get to a cell by going a different route than straight (there is not) than update the cells g score.  Repeat until you reach (10,3) where the heuristic distance will prompt us to go to (11,2) instead of going straight to (11,3) and then go to (12,1) for the final distance and have thus reached your destination. 
So the parents are (3,3) (4,3)(5,3) (6,3)(7,3)(8,3)(9,3)(10,3)(11,2)(12,1)


## Question 3

List out the cells that represent the shortest path you found above. Then list the commands that would need to be sent to the robot to follow this path. The robot in question moves perfectly without any error, and reponds to two commands: it can either move forward a specified number of cells with `move(cells)`, or it can turn with `turn(radians)`. The robot should end at the goal the same direction at which it faced originally.

Listed as above.

	move(1)
	move(1)
	move(1)
	move(1)
	move(1)
	move(1)
	move(1)
	turn(0.785398)
	move(1)
	move(1)
	turn(-0.785398)

