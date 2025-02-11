This repository contains Python codes that systematically explore the entire relevant domain for each type of plan (TS^2, TT^2, and mixed plans).

Each term in the biorthogonal curvature formula is computed explicitly at every sampled point, ensuring that no critical region is overlooked in the analysis.  

We adopted a constrained optimization strategy based on the Sequential Least Squares Programming (SLSQP) algorithm, chosen for its efficiency in handling constraints and its rapid convergence in smooth and differentiable problems like ours. To enhance the robustness of the optimization process, we first employed Differential Evolution (DE) as a global optimization strategy to explore the parameter space and avoid local minima. The solution obtained from DE was then refined via SLSQP, ensuring that the final parameter set maximized the minimum of K_{biort}} while strictly satisfying all imposed constraints.  

The verification of K_{biort} was performed over an extensive set of test cases, including a dense uniform grid and a set of 100,000,000 randomly sampled points, confirming that the biorthogonal curvature remains strictly positive everywhere.
