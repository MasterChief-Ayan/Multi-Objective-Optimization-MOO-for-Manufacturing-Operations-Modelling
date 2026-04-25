# Multi-Objective Optimization: From Brute Force to Standardized  Algorithms

## Overview
In real-world engineering and business, we rarely optimize for a single variable. We want to maximize throughput while minimizing cost, or maximize quality while minimizing time. These are **conflicting objectives**. 

This repository explores how to solve these multi-objective problems using the classic **0/1 Knapsack Problem** (maximizing the value of items in a bag without exceeding a weight limit) as a proxy for complex, real-world system design. 

Instead of searching for one impossible "perfect" solution, this project is built to find the **Pareto Front**: the mathematical set of optimal trade-offs where no single objective can be improved without degrading another (known as "non-dominated" solutions).

## Repository Structure

The project is broken down into three Jupyter Notebooks, progressing from foundational logic to production-ready frameworks:

### Notebook 1: Exhaustive Search (The Brute Force Approach)
* **The Layman Concept:** We try every single combination of items in the knapsack to find the absolute best setups. 
* **The Technical Reality:** This demonstrates **combinatorial explosion**. The time complexity is $O(2^n)$ where $n$ is the number of variables. While this guarantees finding the true Pareto Front, it becomes computationally intractable for anything beyond a trivial number of variables. It proves why we need smarter algorithms for complex problems.

### Notebook 2: Stochastic Search (Genetic Algorithm from Scratch)
* **The Layman Concept:** Since we can't check every combination, we simulate biological evolution. We generate a random "population" of solutions, let the best ones "mate," introduce random "mutations," and evolve better solutions over time.
* **The Technical Reality:** This notebook builds a **Genetic Algorithm (GA)** entirely from scratch in Python to bypass the $O(2^n)$ scaling issue. It implements the core heuristic operators:
    * **Crossover:** Combining arrays of parent variables to exploit known good regions of the search space.
    * **Mutation:** Random bit-flipping to maintain genetic diversity and prevent the algorithm from getting trapped in local optima.
    * **Selection:** Evaluating the population using **Pareto Dominance Ranking** to select non-dominated solutions for the next generation's mating pool.

### Notebook 3: The DEAP Framework (Industry Standard)
* **The Layman Concept:** Instead of writing all the evolutionary rules by hand, we use a professional, pre-built toolkit to do the heavy lifting faster and with less code.
* **The Technical Reality:** This notebook solves the exact same problem utilizing **DEAP** (Distributed Evolutionary Algorithms in Python). Specifically, it implements the **NSGA-II** (Non-dominated Sorting Genetic Algorithm II). This is the industry-standard algorithm for multi-objective optimization, utilizing fast non-dominated sorting and crowding distance calculations to maintain a highly diverse and accurate Pareto Front.

## Application: Beyond just a standard Knapsack
While this repository uses the Knapsack Problem for simplicity, the NSGA-II engine built in Notebook 3 is entirely agnostic. By swapping out the objective functions (Weight/Value), this exact architecture can be used to optimize complex industrial systems—such as minimizing a factory's **Annual Running Cost ($)** against its **Total Required Investment ($)** and **Buffer Capacity**, outputting actionable, data-driven decisions.
