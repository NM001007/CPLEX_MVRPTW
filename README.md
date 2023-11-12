# CPLEX_MVRPTW
A cplex code for multi-vehicle multi-depot version of CVRP with time windows

Hi, this is an implementation of CPLEX that can be applied on multi-depot and multi-vehicle veriosn of CVRPTW. The main file initially reads the provided data, which is an instance of Solomon dataset. However, you can apply it on any routing instance or even randomly generating one. 

# Model Definition
Here are the formulations used for the objective function and the constraints:

## Objective Function
Typically considered in the vehicle routing problem, the objective function tries to minimize the overall distance of the routes taken by the vehicles. 

$$ Minimize\sum_{k=1}^K \sum_{i=0}^{n} \sum_{j=0}^{n} c_{ijk} x_{ijk}$$

## Constraints <br>
The followings are the paramters considered in modeling the problem: <br>
N: Number of Customers <br>
K: Number of Vehicles <br>
V: Number of Vertices (including both depots and customers) <br>
A: List of all the possible edges in the graph $(i, j) \quad i, j \in V$ <br>
M: A large positive number <br>

**Customer Visit Constraint** <br>

$$\sum_{j \in V }  x_{ij}^{k} = y_{i}^{k}, \quad \forall \, \,  i \in N; \, k \in,  K;$$ <br>

$$\sum_{k \in K } y_{i}^{k} = 1, \quad \forall \, \,  i \in N;$$ <br>


**Route and Flow Conservation, and Depot Constraints** <br>

$$\sum_{j \in V }  x_{ih}^{k} - \sum_{j \in V }  x_{hj}^{k} = 0 \quad \forall \,  h \in N; \, k \in, K.$$ <br>

$$\sum_{d \in D} \sum_{(i,j) \in A; i \in D}  x_{ij}^{k} \leq 1, \quad k \in K$$ <br>

$$\sum_{d \in D} \sum_{(i,j) \in A; j \in D}  x_{ij}^{k} \leq 1, \quad k \in K,$$ <br>

**Capacity Constraint**<br>
$$\sum_{i \in N} d_i y_{i}^{k} \leq Q, \quad \forall \, k \in K$$<br>

**Time Constraints**<br>
$$\tau_{j}^{k} \geq \tau_{i}^{k} + s_{i}^{k} + t_{ij} - M(1 - x_{ij}^{k}) \quad \forall \, \, i, j \in V \, k \in K;$$<br>

$$a_i y_{i}^{k} \leq \tau_{i}^{k} \leq b_i y_{i}^{k}, \quad \forall \, \, i \in C, k \in K$$<br>

$$\sum_{(i,j) \in A} t_{ij} x_{ij}^{k} \leq T, \quad \forall \, \, k \in K.$$<br>

$$t_{0k} = 0, \quad \forall \, \, k \in K.$$<br>

and **Each vehicle should start its new route from a depot where it has returned**.<br>

## Results
The followings are some results returned by the CPLEX problem solver. As I have considered a time limit of 20-30 minutes, these can be feasible solutions rather than optimal ones when the number of customers exceed 10.

![Result for 18 customers, 3 vehicles and 2 depots](https://github.com/NM001007/CPLEX_MVRPTW/blob/main/MVRPTW_Results/MDMVRP_18_3_2.png)

<br>

![Result for 20 customers, 3 vehicles and 2 depots](https://github.com/NM001007/CPLEX_MVRPTW/blob/main/MVRPTW_Results/MDMVRP_20_3_2.png)

<br>

![Result for 25 customers, 3 vehicles and 2 depots](https://github.com/NM001007/CPLEX_MVRPTW/blob/main/MVRPTW_Results/MDMVRP_25_3_2.png)




