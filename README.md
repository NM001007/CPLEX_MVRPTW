# CPLEX_MVRPTW
A cplex code for multi-vehicle multi-depot version of CVRP with time windows

Hi, this is an implementation of CPLEX that can be applied on multi-depot and multi-vehicle veriosn of CVRPTW. The main file initially reads the provided data, which is an instance of Solomon dataset. However, you can apply it on any routing instance or even randomly generating one. 

# Model Definition
Here are the formulations used for the objective function and the constraints:

## Objective Function
Typically considered in the vehicle routing problem, the objective function tries to minimize the overall distance of the routes taken by the vehicles.

$$ Minimize\sum_{k=1}^K \sum_{i=0}^{n} \sum_{j=0}^{n} c_{ijk} x_{ijk}$$

## Constraints

** Customer Visit Constraint **
$$ 
\sum_{j \in V }  x_{ij}^{kw} = y_{i}^{kw}, \forall \, \,  i \in C; \, k \in,  K; \, w \in W,
\sum_{k \in K } \sum_{w \in W } y_{i}^{kw} = 1, \quad \forall \, \,  i = 1,...,n,
$$



