# CPLEX_MVRPTW
A cplex code for multi-vehicle multi-depot version of CVRP with time windows

Hi, this is an implementation of CPLEX that can be applied on multi-depot and multi-vehicle veriosn of CVRPTW. The main file initially reads the provided data, which is an instance of Solomon dataset. However, you can apply it on any routing instance or even randomly generating one. 

# Model Definition
Here are the formulations used for the objective function and the constraints:

## Objective Function
Typically considered in the vehicle routing problem, the objective function tries to minimize the overall distance of the routes taken by the vehicles.

$$ Minimize\sum_{k=1}^K \sum_{i=0}^{n} \sum_{j=0}^{n} c_{ijk} x_{ijk}$$

## Constraints <br>
N: Number of Customers <br>
K: Number of Vehicles <br>
V: Number of Vertices (including both depots and customers) <br>

**Customer Visit Constraint** <br>

$$\sum_{j \in V }  x_{ij}^{k} = y_{i}^{k}, \forall \, \,  i \in N; \, k \in,  K;$$ <br>

$$\sum_{k \in K } y_{i}^{k} = 1, \quad \forall \, \,  i \in N;$$ <br>


**Route and Flow Conservation** <br>

$$\sum_{j \in V }  x_{ih}^{k} - \sum_{j \in V }  x_{hj}^{k} = 0 \forall \, \,  h \in N; \, k \in, K.$$




