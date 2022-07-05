# path_planning_hw
Written by: Scott Mackinlay

## The Context
Here at Machina, we use giant robots to bend and fold metal into all sorts of different shapes. To do that, we need to supply our robots with a path, in form of a list of co-ordinate points, to travel through. The robots run through those points, moving from one point to the next, each in a fixed time step. This means that the time to complete a path of points is directly proportional to the number of points in that path. Because fast robots help us form more parts, we need to go fast. Real fast! 

I've got a parametrized curve that represents a section of a path, and we need to know how quickly we can get the robots to execute that curve. 

Here is one of our robots moving at ~10ft/sec for inspiration:
![i_am_speed](i_am_speed.gif?raw=True)

Check out our [website](https://www.machinalabs.ai/home/) for more context on out process

While definitely not required, consider looking up parametrized curves and robot trajectory planning if you are totally new to this space. 

## The Contraints
In theory, providing just two points - the starting and ending coordinates, would allow the robot to complete the path in least amount of time. However, there are some constraints that you should know about:
- We must start and end with a speed of 0. See how this is calculated in assess_answer(). 
- We must not exceed a discrete cartesian acceleration magnitude (length/time^2) of 0.1. See how this is calculated in assess_answer(). 
- The section of path is represented as a a parametrized curve. We must start at the curve parameter of 0 and end at the parameter of 1.

I've written two functions - eval_curve() and assess_answer(), as part of this assignment. You'll find these in eval_tools.py. eval_curve() generates the parametrized curve (path) by using the set of parameters you provide it as input. assess_answer() will check your submission against the above-mentioned constraints and others to assess the quality of your answer. 

 ## The Ask
What I want is an array of parameters that pass the checks in assess_answer(). Here is an example submission:

```
import numpy as np
from eval_tools import assess_answer
constant_speed = np.concatenate(([0], np.linspace(0, 1, 130), [1]))
assess_answer(constant_speed)
```

This answer uses 132 points, so it's going to take a while for the robots execute all of those points. Since we want really fast robots this answer isn't great and is far from optimal. 

## The Assessment
- The main goal of this assignment is to give me the shortest array of parameters that you can find that pass the checks in assess_answer() for the specific curve described in eval_curve(). 

- You are encouraged to document your assumptions about the types of other curves that your solution could work for. 

- I'm going to be looking for methodical strategy, performant algorithms, and general code quality in addition to the fastest/shortest array of parameters that you can find.

- Try to spend less than ~4hrs on this, but if you do run over on time just lemme know how long it took. 

- The functions that I've provided are written in python (3.8) with substantial reliance on numpy (1.21.5), but you can translate/complete this in whatever language/toolset you think is appropriate. 

## The Submission
In order to submit the assignment, do the following:

1. Navigate to GitHub's project import page: [https://github.com/new/import](https://github.com/new/import)

2. In the box titled "Your old repository's clone URL", paste the homework repository's link: [https://github.com/Machina-Labs/path_planning_hw](https://github.com/Machina-Labs/path_planning_hw)

3. In the box titled "Repository Name", add a name for your local homework (ex. `path_planning_soln`)

4. Set privacy level to "Public", then click "Begin Import" button at bottom of the page.

5. Develop your homework solution in the cloned repository and push it to Github when you're done. Extra points for good Git hygiene.

6. Send us the link to your repository.





