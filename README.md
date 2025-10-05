# hecate-optimal-path

> This algorithm implementation is for [nasa-hecate](https://github.com/AutoML-NASA/nasa-hecate) projects

<img width="3252" height="2184" alt="그림2" src="https://github.com/user-attachments/assets/6659b139-6b28-411c-ae88-35b63f8d0855" />

This repository implements the pathfinding algorithms used in the nasa-hecate project, a game where users find optimal routes on the Moon.

Our initial plan was to use the **D\* Lite algorithm** to simulate pathfinding in a dynamic environment, similar to how a real-world exploratory rover would operate. The primary advantage of D\* Lite is its efficiency in replanning routes when new obstacles are discovered or terrain information changes in real-time.

However, after reviewing the nature of the Apollo missions, we determined that the routes were meticulously pre-planned based on extensive survey data. The mission environment was effectively **static**, without unexpected changes to the terrain during traversal. Consequently, the goal of Project Hecate—reconstructing a single optimal path from a known dataset—is better aligned with a static search algorithm.

For this reason, we chose to implement the **A\* algorithm** to find the optimal routes. A\* is highly efficient and guarantees the shortest path in a static environment, which perfectly suits the context of this project.

---

### A\* vs. D\* Lite Algorithm Comparison

| Feature             | A\* (A-Star)                                                                                             | D\* Lite (Dynamic A-Star Lite)                                                                          |
| :------------------ | :------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------ |
| **Core Concept** | **Optimal pathfinding in a static environment.** | **Fast replanning in a dynamic environment.** |
| **Primary Use Case**| Environments with unchanging maps (e.g., games, initial route calculation in GPS).                       | Environments where map info changes in real-time (e.g., robotics, autonomous drones).                   |
| **Pros** | - Guarantees the shortest path in a static environment.<br>- Relatively simple and intuitive to implement. | - Avoids full recalculation when the path is blocked.<br>- Efficiently updates only affected path segments. |
| **Cons** | - Inefficient in dynamic settings; requires a full path recalculation if an obstacle appears.             | - More complex to implement than A\*.<br>- Can be less efficient than A\* in a purely static environment.   |

### Commonalities Between A\* and D\* Lite

- Both use a **heuristic function** to guide the search efficiently.
- Both use a **cost function** (`f=g+h`) to evaluate nodes.
- Both are **graph-based** search algorithms.
- Both use a **priority queue** to explore the most promising nodes first.

---

## Input Data
Use SLDEM2015 data(SLDEM2015_512_00N_30N_000_045) map

### Official Docs
https://pgda.gsfc.nasa.gov/products/54

### Download Site
https://imbrium.mit.edu/BROWSE/SLDEM2015/TILES/
