# path_planning_hw
Written by: Scott Mackinlay

## The Context
Here at Machina, we use giant robots to bend and fold metal into all sorts of different shapes. To do that, we need to supply our robots with a list of points to execute. The robots run through those points, executing one commanded point per fixed time step. This means that the time to complete a path of points is directly proportional to the number of points in that path. 


Because fast robots are cool (and help us form more parts), we need to go fast. Real fast. I've got a curve that represents a section of a path, and we need to know how quickly we can get the robots to execute that curve. 

Here is one of our robots moving at ~10ft/sec for inspiration:
![i_am_speed](i_am_speed.gif?raw=True)

Check out our [website](https://www.machinalabs.ai/home/) for more context on out process

## The Contraints
I know what you're thinking: just put one point at the beginning of the curve, and one point at the end. Two points wont take very long to execute, right? And while that is the fastest we could "interpret" a curve, there are some constraints that you should know about:
- We must not exceed a discrete cartesian acceleration (length/time^2). You can see what that threshold is and how it is calculated in assess_answer() (more on this in a sec).
- We must start and end with a velocity of 0
- The section of path is a parameterized curve. We must start at the curve parameter of 0 and end at the parameter of 1

I've written two functions to help you get going: eval_curve() and assess_answer(). You'll find these in eval_tools.py. assess_answer() will check your submission against these (and other) constraints and tell ya how you're doing. eval_curve() represents a parameterized spiral; read its documentation if you have questions. 

 ## The Ask
What I want is an array of parameters that pass the checks in assess_answer(). Here is an example submission:

```
import numpy as np
from eval_tools import assess_answer
constant_speed = np.concatenate(([0], np.linspace(0, 1, 130), [1]))
assess_answer(constant_speed)
```

This answer uses 132 points, so it's going to take a while for the robots execute all of those points. I'm pretty sure I said we want really fast robots, so this answer isn't great and is far from optimal. 

## The Assessment
- The main goal of this assignment is to discover the smallest list of parameters for the curve described in eval_curve(). Feel free to look at the guts of eval_curve() for insight, but a good solution not only work for the curve I've provided, but also be generally curve agnostic. You are encouraged to document your assumptions about the types of additional curves that your solution could work for. 

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





