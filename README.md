This Repository contains Python codes that systematically explore the entire relevant domain for each type of plane ( TS^2, TT^2, and all possible combinations for mixed planes). For accurate numerical verification, we set the parameters as follows:
a=5, b=2, c=20, and K_biort=50.
Each term in the biorthogonal curvature formula is computed explicitly at each point in the domain, ensuring that no critical value is neglected.

To achieve rigorous global minimization, we employ Differential Evolution (DE), a stochastic optimization algorithm that is particularly effective for complex high-dimensional landscapes, regardless of convexity.

We further improve robustness by setting a strict stopping criterion (tolerance \(10^{-12}\)), allowing a large number of iterations, and ensuring a sufficiently dense search grid to minimize discretization errors. Consequently, the codes rigorously identify the minimum value of the biorthosual curvature, confirming that the positivity condition is globally valid.
