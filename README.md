# Cube World
# Cube Interior Design Optimization
This repository contains the Python implementation for the optimization of tube paths inside a cube containing three functioning spheres. The project focuses on maximizing an objective function that represents the optimal interaction of tube paths and spheres while satisfying various geometric constraints. The project is based on the principles of optimum design and utilizes advanced numerical optimization techniques to find the best tube paths.

<p align="center">
  <img width="900" src="https://github.com/Amir-M-Vahedi/Cube_World/assets/115154998/a2bc5ba6-2707-45a3-b5db-8d523798b340">
</p>

## Project Overview

The challenge involves designing the interior of a cube containing three functioning parts: a red sphere, a blue sphere, and a green sphere. Additionally, there are four tubes that need to be routed through the cube: red, blue, green, and grey. The red, blue, and green tubes must connect to their respective colored spheres, while the grey tube must avoid touching any of the spheres or other tubes. Importantly, these tubes must not cross or intersect, maintaining a minimum distance of 0.05 units from each other. The goal is to optimize the paths of the tubes to achieve the highest possible score based on interactions among the tubes and spheres.

### Design Variables

The design variables control the specific paths of the tubes through the cube, initially represented by 63 variables which were later reduced to 9 variables through dimensionality reduction techniques.

### Objective Function

The objective function is formulated to maximize the optimal interaction of the tube paths and spheres while minimizing the total length of the tubes. The function evaluates the following:
<p align="center">
$f(D_{rbs}, D_{gc}, l, D_{bg}) = D_{rbs} + (1-D_{gc}) + \frac{5}{l} + D_{bg}$
</p>

where:
- **$D_{rbs}$ :** Closest distance between the red curve and the blue sphere.
- **$D_{gc}$ :** Closest distance between the green curve and the sides of the unit cube.
- **$l$ :** Total length of all curves.
- **$D_{bg}$ :** Distance between the blue curve and the green curve along its entire length.

### Constraints
Ensuring the geometric constraints and interactions are valid:
1. **Non-intersecting Tubes:** Tubes must not cross or intersect.
2. **Distance Constraints:** Minimum distance of 0.05 units between any two tubes.
3. **Bounding Constraints:** Tubes must remain within the cube.
4. **Connectivity Constraints:** Each tube must connect to its respective sphere.

## Optimization Approach

Utilizing `scipy.optimize.minimize` with the `trust-constr` method, this project effectively handles the constraints and ensures the optimization process adheres to the problem's requirements. The `trust-constr` method is a trust-region algorithm suitable for managing both equality and inequality constraints.

## Results and Analysis

Based on the assumption to reduce the dimensionality of the problem, the initial condition was modified to create a near-optimal starting point. This modification, shown in the figure below, includes straightened parts controlled by the optimizer. However, the initial condition was infeasible due to collisions between the curves.

<p align="center">
  <img width="900" src="https://github.com/Amir-M-Vahedi/Cube_World/assets/115154998/6dcdf18b-be08-40b5-ab3a-d15226413120">
</p>

The optimization process yielded a final design with the highest objective function score of 2.804 with a total length of 7.71 units. The final design is shown in the figure below.

<p align="center">
  <img width="900" src="https://github.com/Amir-M-Vahedi/Cube_World/assets/115154998/b33ce872-c66e-4751-a447-be95637996ea">
</p>

## Lessons Learned

Several important lessons were learned throughout this challenge:
- **Dimensionality Reduction:** By reducing the dimensionality of the problem, we can achieve better solutions with less computational cost.
- **Constraint Management:** Properly handling constraints is crucial in optimization problems. Adding terms related to the constraints into the objective function and turning the problem into an unconstrained optimization problem can help the optimization process progress and escape from local or infeasible solutions.
- **Initial Conditions:** The importance of the initial condition to the final converged solution cannot be overstated. A well-chosen initial condition can significantly improve the optimization process and the quality of the final solution.
- **Algorithm Selection:** Choosing an appropriate optimization algorithm can significantly impact the efficiency and effectiveness of the solution.
- **Iterative Refinement:** Continuous refinement and evaluation are essential to achieving optimal results.
- **Visualization:** Visualizing the design helps in understanding the interactions and potential issues with the paths.
