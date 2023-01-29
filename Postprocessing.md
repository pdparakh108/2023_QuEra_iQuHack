In many cases, after the adiabatic algorithm is completed, the graph will have converged to an invalid solution due to the inherent stochastic nature of the process. In these cases, however, we do not necessarily need to discard the shot. Although we may not have reached a maximally independent set, it is still likely that the algorithm will have converged towards some sort of low energy minima. To this end we introduce a classical postprocessing algorithm, which takes an incomplete result, and attempts to patch it.

The algorithm consists of three main steps:

1. Find any instances of two adjacent Rydberg states on the graph, and set both of them to ground.
2. Find every ground state that could become Rydberg without violating the independence condition.
3. Iterate through all combinations of replacing ground states with Rydberg until an MIS solution is found.

![Postprocessing Flow](postprocessingflow.png)

It is important to note that this algorithm is $O(2^n)$ where $n$ is the number of ground states that have the potential to be Rydberg. Therefore for large graphs it has the potential to take an immensely long time, and so we place a cut-off dependent on the number of potentially excitable states. We choose this to be $20$ to find MIS solutions in nearly all cases while still taking fewer than a couple seconds. 
