<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

# CS 4820 Algorithms

This is a study note for CS 4820: algorithms. It is meant to be a summary of crucial materials in the course. This was the first time that I wrote notes like this in English.

## 1 Greedy Algorithms

### 1.1 Problem: Interval Scheduling

#### The Problem

There are n requests that occupy time intervals. Each of them starts at s(i) and ends at f(i). Only one request could be processed at a time. Find the maximum amount of requests that could be scheduled without time intervals overlapping with each other.

#### The Design

While scheduling, always choose the first compatible interval with the least f(i)'s.

#### The Analysis

Proof: By "Stays Ahead" Method. We prove that among all possible solutions, our solution has the least f(i) for every i. Then we prove by contradiction that our solution is optimal.

Run Time: O(n log n), from sorting.

### 1.2 Problem: Minimize Lateness Scheduling

#### The Problem

All intervals are available from point s. Each has length t(i) and deadline d(i). Scheduling intervals after the deadline will have a lateness penality proportional to lateness time. Only one interval can be processed at a time. All intervals should be scheduled. Find a scheduling of these intervals such that the total lateness is minimized.

#### The Design

Always schedule the one with the earliest deadline first.

#### The Analysis

Proof: By "Exchange" Method. First we prove that there is an optimal solution O with no idle time. Then we prove that invert the scheduling of all intervals with deadlines against the "fully sorted order" will not increase total lateness. Since intervals can be inverted up untill become fully sorted by their deadlines, our solution is proved to be at least as good as optimal.

### 1.3 Problem: Graph Shortest Paths

#### The Problem

In a graph where each edge is weighed by l(e) non negative, find a path from s to v with the lowest sum of l(e)'s.

#### The Design: Dijkstra's Algorithm

Starting from s. Add all nodes already explored to a set S. For each node j with at least an edge connecting to S, refresh its distance to s using

![d'[v] = min_{e = (u, v): u \in S} d(u) + l_{e}](https://latex.codecogs.com/gif.latex?d%28v%29%20%3D%20min_%7Be%20%3D%20%28u%2C%20v%29%3A%20u%20%5Cin%20S%7Dd%28u%29%20&plus;%20l_e)
