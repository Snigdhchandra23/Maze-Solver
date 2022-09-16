# Maze-Solver
It is a maze solving robot that uses depth first search algorithm to map the maze and calculate the shortest path from start to destination using flood fill algorithm.
It uses ultrasonic sensors for calculating distance form walls and then processing this data to navigate through the maze.

https://user-images.githubusercontent.com/54740532/190594092-426bfe80-d6ff-4f46-a19d-55bd7fb02160.mp4


#Developing the algorithm from scratch:

We used a 2D array of size 16*16 that was started with zeros to simulate the maze. It will be known as the maze array.

The robot can move while looking in four directions when it is in the maze (orientations). We created a variable called Orient to store one of the four values 0, 1, 2, 3 to represent this in the algorithm. The orient variable is changed each time the robot makes a turn.
![orientation](https://user-images.githubusercontent.com/54740532/190598670-97c1376a-4fa8-462e-ab52-05cb051d43a3.jpeg)

Next, we allocated various numbers to the various wall arrangements that a square can have. There are 16 possible wall configurations (including a square with all four walls, and with no walls at all).
![walls config](https://user-images.githubusercontent.com/54740532/190598879-2442229e-33ea-471d-9562-2b6b591855e9.jpeg)

With the aid of its distance sensors, the car can determine whether there are walls to its left, right, or front as it moves through the maze. Next, we changed the relevant entry in the maze array by its wall configuration based on whether a wall was present to the cars's left, right, or front as well as the cars's orientation within the cell.
These 16 permutations were then divided into groups based on whether there was a wall in the square to the left, right, up, or down.


#The FloodFill algorithm:

Imagine filling the maze's final location with water ( which is the four centre cells surrounded by 7 walls). The cell that is closest to the destination cells will receive the water first. and then to its nearby cells that are easily accessible. Similar to how water flows through a maze, it will finally reach the car's starting place.

Another 16x16 maze is defined; let's call it the Flood array. We allocated zeros to the four destination cells, one to the cell that is immediately accessible by the destination cells, and so on, taking our cue from the water pouring scenario. The cells with the largest number are those to which the water flows last.
![flood array](https://user-images.githubusercontent.com/54740532/190599600-2aebe1b3-51e7-4390-b2a9-5ae9768fd4db.png)
The car will finally reach the destination in the path that requires the fewest number of cells if you set it anywhere in the maze and instruct it to go to the cell whose value is 1 less than the cell it is in.

#The Traversal

However, when your car first enters the maze, it assumes there are no walls at all because it is unaware of the wall configuration. (Aside from the walls at the maze's edges). Your Flood array appears as shown.
![traversal](https://user-images.githubusercontent.com/54740532/190600057-efb17532-071c-48cf-b143-90605a6d4097.png)

As the car continues moves through the maze,

1) Finds the values of it’s neighboring cells (from the flood array)
2)Travels to the neighboring cell with the least value.
3) Detects the walls to its left, right and the front
4) Updates the newly found walls in the maze array
5) Perform the flood fill for the entire flood array
6) Back to step 1, and continue until the robot moves to the desired position.

#At last The Quick Run

You can move the car back to the starting square and perform the quick run once you've determined that it has found enough cells to establish an ideal path. The method involves the car discovers the values of the cells that are nearby (from the flood array) travels to the adjacent cell that has a value that is one less than the current cell.
Return to step 1 and repeat the process until the robot reaches the desired position.
Since the car will only be travelling to the cells that have already been detected during the quick run, neither the maze array nor the flood array need to be updated.

Thank You!
