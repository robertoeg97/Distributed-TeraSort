# Distributed TeraSort

Due to academic integrity, the project source code and detailed report are private. This public summary outlines the core objectives, challenges, and achievements. Code/reports cannot be shared, even on request.

## Project Overview

This project implements a distributed sorting algorithm inspired by the TeraSort benchmark, designed for high-performance computing clusters. The primary challenge addressed is sorting massive datasets that exceed the memory capacity of a single machine, leveraging the combined memory and processing power of multiple nodes in a cluster.

## Problem Statement

Given a large dataset composed of fixed-size records (each with a 10-byte key and 88-byte value), the goal is to efficiently sort the entire dataset in ascending order by key. The dataset is distributed across several nodes, and the solution must ensure scalability, correctness, and high performance, even when the data cannot fit into the memory of any single node.

## High-Level Design

- **Distributed Memory Model:** Utilizes MPI (Message Passing Interface) for inter-node communication, enabling parallel processing across multiple machines.
- **Parallel Sorting:** Each node sorts its local data and participates in a global partitioning and redistribution phase to ensure the final output is globally sorted.
- **Sample Sort Paradigm:** The algorithm selects representative samples to determine partition boundaries (splitters), minimizing data movement and balancing the workload across nodes.
- **Hybrid Parallelism:** Explored both distributed (MPI) and shared-memory (OpenMP) parallelism to accelerate local sorting.
- **Scalability:** Designed to efficiently handle increasing data sizes and node counts, with careful attention to communication patterns and memory usage.

## Implementation Notes

- **OpenMP Parallelization:** I implemented a custom parallel sample sort using OpenMP to accelerate the local sort step within each node. This approach aimed to leverage all available CPU cores for improved performance.
- **Fallback to qsort():** In practice, the final testing environment assigned multiple MPI processes per physical machine, limiting the number of threads available to each process. As a result, the potential speedup from OpenMP parallelization was minimal, and the highly optimized standard library `qsort()` outperformed the custom parallel sort in this context. 

## Project Responsibilities

- Designing and implementing the distributed sorting logic, including data partitioning, sample selection, and inter-node data exchange.
- Developing and optimizing both serial and parallel (OpenMP) local sorting routines.
- Evaluating performance trade-offs between custom parallel sorting and standard library routines under different cluster configurations.
- Creating and executing test cases to validate correctness and measure performance on both local and cluster environments.
- Analyzing performance metrics, identifying bottlenecks, and documenting the project.

## Skills & Technologies

- **MPI (Message Passing Interface)**
- **OpenMP (Shared-memory Parallelism)**
- **C Programming**
- **Parallel and Distributed Algorithms**
- **Performance Analysis and Optimization**
- **Linux Cluster Computing**

## Learning Outcomes

- Gained hands-on experience designing scalable algorithms for distributed memory systems.
- Deepened understanding of parallel sorting techniques and their practical challenges.
- Developed proficiency in MPI and OpenMP programming for high-performance computing.
- Enhanced skills in debugging, profiling, and optimizing distributed applications.
