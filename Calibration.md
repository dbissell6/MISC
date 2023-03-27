The Calibration challenge required the player to find the center of a circle on a coordinate plane with a range of -1 billion to +1 billion (x and y). The player was given 300 chances to find the center of the circle, and each guess the player received a detected or undetected response indicating whether their guess fell within the radius of the circle. The challenge consisted of 47 calibration iterations, with each iteration requiring the player to find a single point in the map that would be used as a reference. The calibrator could point at any location in the map and detect if its pointing at the reference point, or if the reference point is within its radius or not. The calibrator could only run up to 300 times in each iteration, and if the reference point was not found within 300 attempts, the calibrator stopped and the process had to be restarted. The coordinates (X, Y) of the reference point, as well as the radius R of the calibrator were unknown in each iteration. The calibrator had error correcting capabilities so it could point up to 2 galactic units away from the reference point and still return a REFERENCE response.

![image](https://user-images.githubusercontent.com/50979196/227996889-e093cafb-8517-4e05-964d-0efd4d14178d.png)
![image](https://user-images.githubusercontent.com/50979196/227996985-e05ffcb0-7eee-48a5-b925-ccaf067d3cd5.png)
![image](https://user-images.githubusercontent.com/50979196/227997066-2cb6e131-6ff1-4e7b-af43-9d05e2c4b7ad.png)


My strategy to solve this had two main parts.
1)    Seed the field: I used about half of my guesses to get a rough estimate of the center of the circle by identifying each point that was detected as a hit. Then, I found the four points with the minimum and maximum x and y values among the hits, and took the midpoint of these points as the initial guess for the center of the circle.

2)    Expand the circle: Starting with the x-max direction, I used a binary search algorithm to iteratively expand the circle in each direction. For each iteration, I found the midpoint between the hit with the greatest x value and the miss with the smallest x value that is still greater than the maximum hit x value. Then repeated for each direction. This strategy is similar to the "guess a number from 1-100" problem, where guessing midpoints allows one to guarantee the correct answer after six guesses.

Step 2 iterates for each direction ~20 times.
![image](https://user-images.githubusercontent.com/50979196/227999631-12d8e6f9-9658-4bd5-bccc-4407d2578439.png)

Each hit at this stage will move the boundaries, thus generating a new guess of center of the circle. 
![image](https://user-images.githubusercontent.com/50979196/227999137-45f9fe4b-7341-45d4-b478-0c3ea8c718fd.png)
![image](https://user-images.githubusercontent.com/50979196/227999304-612942a5-7ce3-401c-9c67-6a289a3590e3.png)

![image](https://user-images.githubusercontent.com/50979196/228016619-d059527d-32a4-4929-a230-4cdf6cd29563.png)


