# Vehicle Routing Problem (VRP) Solver

This Python implementation provides a comparative analysis of two metaheuristic algorithms - Tabu Search and Simulated Annealing - for solving the Vehicle Routing Problem (VRP). The solver helps optimize delivery routes for a fleet of vehicles serving multiple customers while respecting vehicle capacity constraints.

## Features

- Implementation of two metaheuristic algorithms:
  - Tabu Search with customizable tabu tenure
  - Simulated Annealing with adjustable temperature parameters
- Random problem instance generation with configurable parameters
- Comprehensive solution visualization including:
  - Convergence graphs comparing both algorithms
  - Geographic visualization of routes
  - Detailed performance metrics and solution statistics

## Requirements

The implementation requires the following Python packages:
- NumPy: For efficient numerical operations
- Matplotlib: For visualization
- Random: For stochastic operations
- Time: For performance measurement
- Copy: For deep copying of solutions

## Usage

### Basic Usage

```python
from vrp_solver import run_vrp_comparison

# Run comparison with default parameters
run_vrp_comparison()

# Run with custom parameters
run_vrp_comparison(
    num_customers=20,
    num_vehicles=6,
    vehicle_capacity=100,
    area_size=100,
    max_iterations=100
)
```

### Class Structure

#### VRPSolver Class

The main `VRPSolver` class handles all VRP-related operations:

```python
solver = VRPSolver(
    distances=distances_matrix,
    demands=customer_demands,
    vehicle_capacity=100,
    num_vehicles=5,
    max_iterations=1000
)
```

### Key Methods

1. **Solution Generation**
   - `generate_initial_solution()`: Creates an initial feasible solution
   - `solve_tabu_search()`: Implements the Tabu Search algorithm
   - `solve_simulated_annealing()`: Implements the Simulated Annealing algorithm

2. **Solution Evaluation**
   - `calculate_route_cost()`: Computes cost for a single route
   - `calculate_total_cost()`: Computes total solution cost
   - `check_capacity_constraint()`: Validates vehicle capacity constraints

3. **Neighborhood Operations**
   - `get_neighborhood_moves()`: Generates possible solution modifications
   - `apply_move()`: Executes a specific modification to a solution
   - `is_feasible()`: Checks if a solution satisfies all constraints

## Problem Generation

The `generate_random_problem()` function creates random VRP instances with:
- Random customer locations in a 2D space
- Random customer demands
- Euclidean distance calculations

## Visualization

The implementation provides two types of visualizations:

1. **Convergence Plots**
   - Shows the progression of solution quality over iterations
   - Compares convergence patterns between Tabu Search and Simulated Annealing
   - Highlights final solution costs

2. **Route Visualization**
   - Geographic representation of calculated routes
   - Color-coded routes for each vehicle
   - Clearly marked depot and customer locations

## Performance Metrics

The solver outputs comprehensive performance metrics including:
- Solution cost for each algorithm
- Computation time
- Number of routes generated
- Detailed route information (demands and costs)
- Solution convergence patterns

## Parameter Tuning

### Tabu Search Parameters
- `tabu_tenure`: Controls the number of iterations a move remains tabu (default: 20)
- `max_iterations`: Maximum number of iterations (default: 1000)

### Simulated Annealing Parameters
- `initial_temp`: Starting temperature (default: 1000)
- `cooling_rate`: Rate of temperature decrease (default: 0.95)
- `max_iterations`: Maximum number of iterations (default: 1000)

## Implementation Details

### Move Types
The implementation supports three types of neighborhood moves:
1. `swap_within`: Exchanges positions of two customers in the same route
2. `swap_between`: Exchanges customers between different routes
3. `relocate`: Moves a customer from one route to another

### Solution Representation
- Solutions are represented as lists of routes
- Each route is a list of customer indices
- Routes start and end at the depot (index 0)

## Example Output

The solver provides detailed output including:
```
Comparación de Resultados:
------------------------------------------------------------
Método               Costo         Tiempo (s)   Rutas         
------------------------------------------------------------
Búsqueda Tabú        534.21        2.45        6
Recocido Simulado    547.83        1.98        6
------------------------------------------------------------
```

