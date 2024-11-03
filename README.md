# CI2024_lab2
---

# Traveling Salesman Problem (TSP) - Genetic Algorithm and Greedy Approach

This project provides implementations of both a Genetic Algorithm and a Greedy Algorithm to solve the **Traveling Salesman Problem (TSP)** across multiple datasets. The objective of the TSP is to find the shortest possible route that visits a list of cities exactly once and returns to the starting city.

## Table of Contents
1. [Introduction](#introduction)
2. [Algorithms Used](#algorithms-used)
3. [Project Structure](#project-structure)
4. [Results](#results)

## Introduction

The TSP is a classic optimization problem widely studied in computer science and operations research. Here, we solve it using two approaches:
- **Genetic Algorithm**: A metaheuristic inspired by the process of natural selection.
- **Greedy Algorithm**: A heuristic that builds a solution step-by-step, selecting the nearest unvisited city at each step.

The project is organized to compare the effectiveness of these two algorithms on different datasets representing cities in various countries.

## Algorithms Used

### Genetic Algorithm
The Genetic Algorithm (GA) is a stochastic optimization technique that evolves a population of solutions (individuals) over multiple generations to approximate the optimal solution to the TSP.

**Key Steps:**
1. **Initialization**: A population of random tours is generated.
2. **Selection**: Individuals are selected based on their fitness (inverse of total distance).
3. **Crossover**: New offspring are generated using Partially Mapped Crossover (PMX) to combine parts of two parent tours.
4. **Mutation**: Random mutation swaps two cities in an individual's tour to introduce variability.
5. **Survivor Selection**: The population is reduced to the original size, preserving the best individuals.

**Parameters**:
- **Population Size**: 150
- **Generations**: 2000
- **Offspring Size**: 50

### Greedy Algorithm
The Greedy Algorithm is a simpler heuristic that constructs a solution iteratively:
1. Starting from an initial city, it visits the nearest unvisited city until all cities are visited.
2. Returns to the starting city to complete the tour.

While the Greedy Algorithm doesn't guarantee an optimal solution, it provides a good baseline for comparison.

## Project Structure

- `compute_DIST_MATRIX`: Creates a symmetric distance matrix using the geographic coordinates of cities.
- `genetic_algorithm`: Implements the Genetic Algorithm for TSP.
- `greedy_algorithm`: Implements the Greedy Algorithm for TSP.
- `datasets`: A list of CSV files representing cities in various countries.

## Results

The table below compares the results of the Genetic Algorithm and the Greedy Algorithm for each dataset.

| Dataset             | Genetic Algorithm - Best Distance (km) | Generation Found | Greedy Algorithm - Distance (km) | Steps |
|---------------------|----------------------------------------|------------------|-----------------------------------|-------|
| `cities/italy.csv`  | 5488.39                               | 1348              | 4436.03                           | 46    |
| `cities/vanuatu.csv`| 1345.54                               | 37              | 1475.53                           | 8     |
| `cities/russia.csv` | 89593.53                             | 1999              | 42334.16                          | 167   |
| `cities/us.csv`     | 199003.50                             | 1996              | 48050.03                          | 326   |
| `cities/china.csv`  | 422333.27                             | 1995              | 63962.92                          | 726   |

### Observations
- The Genetic Algorithm generally takes longer to find the best solution, with convergence often close to the maximum number of generations (2000).
- The Greedy Algorithm produces solutions quickly but with higher total distances, indicating that it provides suboptimal results as expected.
- The Genetic Algorithm consistently finds shorter paths than the Greedy Algorithm, albeit with greater computational cost.
