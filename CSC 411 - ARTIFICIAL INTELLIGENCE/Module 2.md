# MODULE 2: PROBLEM SOLVING AND SEARCH
NOTE:
![[Module2.docx]]
## Learning Objectives

By the end of this module, you should be able to:

- **Formulate** real-world problems as formal search problems in a state space.
    
- **Understand and implement** uninformed search algorithms like Breadth-First Search (BFS), Depth-First Search (DFS), and Uniform Cost Search (UCS).
    
- **Understand and implement** informed search algorithms, including A* Search and Greedy Best-First Search.
    
- **Design and evaluate** effective heuristic functions for informed search.
    
- **Analyze** the time and space complexity of different search algorithms.
    
- **Apply** these search algorithms to practical problems such as pathfinding and puzzle solving.
    
- **Implement** various search algorithms proficiently in Python.
    

## Module Structure

- **Theory Session (2 hours):** Covering problem formulation, an overview of search strategies, and the concept of heuristics.
    
- **Practical Lab (2 hours):** Hands-on session focused on implementing search algorithms and applying them to pathfinding challenges.
    

## 1. Problem Solving as Search

### 1.1 What is Problem Solving in AI?

At its core, problem-solving in Artificial Intelligence is about finding a methodical way to get from a starting point to a desired endpoint. We can model this process as a **search**.

> Analogy: Exploring a Maze
> 
> Imagine you're placed at the entrance of a giant maze (initial state). Your goal is to find the exit (goal state). The maze itself, with all its possible corridors and dead ends, represents the state space. Every step you take—forward, left, or right—is an action. The process of exploring the maze to find the exit is exactly what we mean by "search." AI uses algorithms to do this exploration systematically and efficiently.

### 1.2 Components of a Search Problem

To solve a problem using search, we first need to define it formally. Every search problem can be broken down into five key components:

1. **Initial State:** This is the single, specific starting point of the problem.
    
    - _Example:_ In a maze, it's your starting position. For an 8-puzzle, it's the specific tile configuration you begin with.
        
2. **State Space:** This is the set of _all possible states_ or configurations that can be reached from the initial state by any valid sequence of actions.
    
    - _Example:_ In a maze, it's every single square you could possibly stand on.
        
3. **Actions (and Successor Function):** These are the legal moves or operations available from a given state. The **Successor Function** is a function that takes a state as input and returns a set of `(action, resulting_state)` pairs.
    
    - _Example:_ From a square in a maze, your available actions might be `Move North`, `Move South`, `Move East`, `Move West`, but only if there isn't a wall blocking the way.
        
4. **Transition Model:** This defines the result of performing an action in a state. It's the "physics" of the problem environment. It answers the question: "If I am in state `S` and I do action `A`, which state will I be in next?"
    
    - _Example:_ If you are at `Position(x, y)` and you perform the action `Move North`, the transition model tells you that you will end up at `Position(x, y-1)`.
        
5. **Goal Test:** This is a function that determines if a given state is a goal state. The search is complete when an agent reaches a state that passes this test.
    
    - _Example:_ "Am I at the exit of the maze?" or "Do the tiles of the 8-puzzle match the `1-2-3-4-5-6-7-8-blank` configuration?"
        
6. **Path Cost (Optional):** This component measures the cost of a sequence of actions (a path). It's crucial for finding the _best_ solution, not just _any_ solution.
    
    - _Example:_ The number of steps taken in a maze, the total distance traveled in a road trip, or the time taken to complete a task.
        

### 1.3 Problem Formulation Examples

Let's see how to apply these components to formalize a couple of classic AI problems.

Example 1: The 8-Puzzle

The 8-Puzzle is a sliding puzzle that consists of a 3x3 grid with 8 numbered tiles and one blank space.

- **Initial State:** A specific, scrambled arrangement of the tiles.
    
- **State Space:** All 181,440 possible arrangements of the 8 tiles on the 3x3 grid.
    
- **Actions:** Move the blank tile Up, Down, Left, or Right (if the move is within the grid boundaries).
    
- **Transition Model:** Given a state (board configuration) and an action (e.g., `Move Blank Left`), it returns the new board configuration.
    
- **Goal State:** The tiles are arranged in numerical order (e.g., 1-8), with the blank space in a designated corner.
    
- **Path Cost:** The number of moves made. Each move typically has a cost of 1.
    

Example 2: Route Finding

Finding the shortest path between two cities on a map.

- **Initial State:** The starting city (e.g., "Arad").
    
- **State Space:** A graph where the nodes are all the cities on the map and the edges are the roads connecting them.
    
- **Actions:** Drive from the current city to an adjacent city connected by a road.
    
- **Transition Model:** If the agent is in "Arad" and takes the action "Drive to Sibiu," the resulting state is "Sibiu."
    
- **Goal State:** The destination city (e.g., "Bucharest").
    
- **Path Cost:** The sum of the lengths of the roads taken, which could be measured in distance (km) or travel time.

## 2. Search Strategies

Search strategies are the algorithms we use to explore the state space. They are divided into two main categories based on whether they use additional problem-specific knowledge.

### 2.1 Uninformed Search (Blind Search)

These strategies have **no information** about the problem other than its definition. They don't know if one state is "closer" to the goal than another. They are "blind" because they explore systematically without any guidance.

#### Breadth-First Search (BFS)

- **Strategy:** Explores the state space layer by layer. It finds all nodes at depth `d` before moving on to nodes at depth `d+1`.
    
- **Analogy:** Imagine ripples spreading out from a stone dropped in a pond. BFS explores the state space just like that—one "ring" at a time. It uses a **Queue (First-In, First-Out)** data structure.
    
- **Properties:**
    
    - **Complete?** Yes. If a solution exists, BFS is guaranteed to find it.
        
    - **Optimal?** Yes, but only if all actions have the same cost. Since it finds the shallowest goal, it finds the optimal solution in terms of the number of steps.
        
    - **Time Complexity:** `O(b^d)` where `b` is the branching factor and `d` is the solution depth. Can be very slow for large state spaces.
        
    - **Space Complexity:** `O(b^d)`. This is its major drawback, as it must store all nodes at the current depth in memory.
        
- **Best for:** Finding the shortest path in unweighted graphs where memory is not a major concern.

VIDEO EXPLAINATION: https://www.youtube.com/watch?v=HZ5YTanv5QE&pp=ygUUYnJlYWR0aCBmaXJzdCBzZWFyY2g%3D

#### Depth-First Search (DFS)

- **Strategy:** Explores as deeply as possible down one path before backtracking.
    
- **Analogy:** Think of navigating a maze by always taking the leftmost path at every junction. You follow it to a dead end, then backtrack to the last choice and try the next path. It uses a **Stack (Last-In, First-Out)** data structure.
    
- **Properties:**
    
    - **Complete?** No. Can get stuck in infinite loops or very long paths and never find a solution, even if one exists.
        
    - **Optimal?** No. It finds the "leftmost" solution, not necessarily the best one.
        
    - **Time Complexity:** `O(b^m)` where `m` is the maximum depth of the search space.
        
    - **Space Complexity:** `O(bm)`. This is its key advantage. It only needs to store the current path.
        
- **Best for:** Problems where solutions are known to be deep, any solution is acceptable, and memory is limited.
- VIDEO EXPLAINATION: https://www.youtube.com/watch?v=Urx87-NMm6c&pp=ygUUYnJlYWR0aCBmaXJzdCBzZWFyY2g%3D
    

#### Uniform Cost Search (UCS)

- **Strategy:** A smarter version of BFS. Instead of expanding the shallowest node, it expands the node with the lowest path cost (`g(n)`) from the start. It uses a **Priority Queue**.
    
- **Analogy:** It's like a delivery driver who, at each stop, checks the total mileage and always chooses the next stop that results in the lowest overall distance traveled so far.
    
- **Properties:**
    
    - **Complete?** Yes.
        
    - **Optimal?** Yes, always. It is guaranteed to find the path with the lowest total cost.
        
    - **Time Complexity:** `O(b^(1+C*/ε))` where `C*` is the optimal cost and `ε` is the minimum action cost.
        
    - **Space Complexity:** Same as time complexity. Can be large.
        
- **Best for:** Finding the cheapest path when action costs vary (e.g., route finding with different road distances).
- VIDEO EXPLAINATION: https://www.youtube.com/watch?v=dRMvK76xQJI  ,  https://www.youtube.com/watch?v=dRMvK76xQJI
    

### 2.2 Informed Search (Heuristic Search)

These strategies use problem-specific knowledge, in the form of a **heuristic function**, to find solutions more efficiently.

#### Heuristic Functions

A heuristic function, **h(n)**, is an _estimate_ of the cost from the current state `n` to the goal. It's an educated guess to guide the search.

- **Properties of Good Heuristics:**
    
    - **Admissible:** An admissible heuristic **never overestimates** the true cost. It is "optimistic." `h(n) ≤ true_cost(n)`. This is crucial for A*'s optimality.
        
    - **Consistent:** A stronger condition. The cost from a node to the goal must be no greater than the cost of moving to its successor plus the successor's heuristic value. `h(n) ≤ cost(n, n') + h(n')`.
        
- **Common Heuristics:**
    
    - **Manhattan Distance:** For grid worlds. `|x1-x2| + |y1-y2|`. The number of squares you must travel horizontally and vertically.
        
    - **Euclidean Distance:** The straight-line "as the crow flies" distance. `√[(x1-x2)² + (y1-y2)²]`.
        
    - **Hamming Distance / Misplaced Tiles:** For puzzles. The number of tiles not in their correct final position.
        

#### Greedy Best-First Search

- **Strategy:** Expands the node that _appears_ to be closest to the goal. It makes its decision based only on the heuristic `h(n)`.
    
- **Analogy:** A mountain climber who always takes the step that goes highest, hoping it leads to the summit. They might get stuck on a smaller peak because they ignored the overall path.
    
- **Properties:**
    
    - **Complete?** No. Can get stuck in loops.
        
    - **Optimal?** No. It's "greedy" and can be easily tricked by misleading heuristics.
        
    - **Time & Space Complexity:** `O(b^m)`, but a good heuristic can make it very fast.
     
- VIDEO EXPLAINATION:  https://youtu.be/KwBiZIUUtMQ?si=UAOO2w0JgvXtYz2L

#### A* Search

- **Strategy:** The champion of informed search. It combines the strengths of UCS and Greedy search by expanding the node with the lowest **`f(n) = g(n) + h(n)`**, where:
    
    - `g(n)` = the actual cost from the start to node `n` (the UCS part).
        
    - `h(n)` = the estimated cost from `n` to the goal (the Greedy part).
        
- **Analogy:** A smart navigator who considers both the road already traveled (`g(n)`) and the estimated distance left to the destination (`h(n)`) to choose the most promising route.
    
- **Properties:**
    
    - **Complete?** Yes.
        
    - **Optimal?** Yes, if the heuristic `h(n)` is **admissible**.
        
    - **Time & Space Complexity:** `O(b^d)`. It is optimally efficient—no other optimal algorithm is guaranteed to expand fewer nodes.
	     
    - VIDEO EXPLAINATION: https://youtu.be/6TsL96NAZCo?si=AzwHZD9lj6hIgQp2
        
- __Why A_ is Optimal:_* If `h(n)` is admissible, it never overestimates the remaining cost. Therefore, the `f(n)` value of any node on the true optimal path will always be less than or equal to the actual cost of that path. A* will explore along this cheapest path first, guaranteeing it finds the optimal solution before it gets sidetracked by more expensive paths.

# Questions:

  

When would you choose DFS over

BFS? Provide a concrete example.

  

How does the quality of a

heuristic function affect A* performance?

  

What modifications would you

make to A* for real-time pathfinding in games?

  

Compare the search algorithms

in terms of their suitability for different types of problems.

  

How would you handle dynamic environments where

obstacles can appear or disappear?
# Answer
### 1. When would you choose DFS over BFS? Provide a concrete example.

You would choose Depth-First Search (DFS) over Breadth-First Search (BFS) primarily when **memory is limited**.

BFS's major drawback is its space complexity of $O(b^d)$, as it must store all nodes at the current depth in memory. In contrast, DFS's key advantage is its space complexity of $O(bm)$, meaning it only needs to store the current path it is exploring.

A concrete example would be **navigating a very deep maze or a complex puzzle** where solutions are known to be deep. If the maze has many branching paths (a large `b`) and the solution is far from the start (a large `d`), BFS would quickly run out of memory trying to store all possible paths "layer by layer". DFS would be more suitable as long as _any_ solution is acceptable, even if it's not the shortest one.

---

### 2. How does the quality of a heuristic function affect A* performance?

The quality of a heuristic function, $h(n)$, is critical to A*'s performance, primarily affecting its **optimality** and **efficiency**.

- **Optimality:** For A* to be **optimal** (guaranteed to find the best solution), the heuristic must be **admissible**. An admissible heuristic "never overestimates" the true cost to the goal. This property is "crucial" because it ensures A* does not get sidetracked by paths that seem cheap but are actually more expensive.
    
- **Efficiency:** A* is "optimally efficient," meaning no other optimal algorithm is guaranteed to expand fewer nodes. The heuristic acts as an "educated guess" to guide the search. A well-designed heuristic (like Manhattan distance for a grid) provides a more accurate estimate, guiding A* more directly toward the goal and helping it avoid exploring unnecessary states.
    

---

### 3. What modifications would you make to A* for real-time pathfinding in games?

While standard A* is effective, it can be too slow or cause lag spikes in real-time games when a long path is requested. Common modifications focus on speed and adaptability:

- **Time-Slicing (Incremental A*):** Instead of running the entire A* algorithm in a single frame (which causes lag), the computation is spread across multiple game frames. The agent might follow a partial or "good enough" path while the full optimal path is still being calculated in the background.
    
- **Jump Point Search (JPS):** This is an optimization for A* on grid maps. It "jumps" over long, straight, or diagonal lines of open cells instead of evaluating every single cell. This significantly prunes the search space and is much faster than standard A*.
    
- **Hierarchical A* (HPA*):** This method abstracts the map. It divides the game world into large regions and first finds a high-level path between regions. Then, it runs a standard A* search to find a low-level path _within_ each region. This is very efficient for large maps.
    
- **D* Lite:** This algorithm is specifically designed for dynamic environments (see next question). In games, this is useful if the agent discovers new, previously unknown obstacles (like a locked door) and needs to quickly find a new route.
    

---

### 4. Compare the search algorithms in terms of their suitability for different types of problems.

Based on the notes, the algorithms are suitable for different problems:

- **Breadth-First Search (BFS):** Best for finding the **shortest path in terms of steps** (on unweighted graphs) when memory is not a major concern.
    
- **Depth-First Search (DFS):** Best for problems where **memory is limited**, solutions are known to be deep, and finding _any_ solution is acceptable (not necessarily the optimal one).
    
- **Uniform Cost Search (UCS):** Best for finding the **cheapest path** when action costs vary (e.g., route-finding with different road distances). It is guaranteed to be optimal in this scenario.
    
- **Greedy Best-First Search:** Suitable for problems where a fast solution is needed, but **optimality is not required**. It only follows the heuristic $h(n)$ and can be "easily tricked by misleading heuristics".
    
- **A* Search:** Best for finding the **provably optimal and cheapest path** when an admissible heuristic $h(n)$ is available. It combines the strengths of UCS (actual cost $g(n)$) and Greedy search (estimated cost $h(n)$).
    

---

### 5. How would you handle dynamic environments where obstacles can appear or disappear?

Handling dynamic environments is crucial for real-world robotics and complex games. The main challenge is that a pre-calculated path can become invalid. The most common strategies are:

- **Simple Re-planning:** The agent follows its pre-calculated A* path. If it detects a new obstacle (e.g., a "disappeared" path is now blocked), it simply stops, considers its current location as the new _initial state_, and runs a brand new A* search to the goal. This is easy to implement but can be very inefficient and slow.
    
- **Incremental Search (D* Lite):** This is a more advanced and efficient family of algorithms (D* stands for "Dynamic A*"). D* Lite is specifically designed for this. It runs an initial search (similar to A*) to find a path. When an obstacle appears or disappears, it doesn't throw away all its work. Instead, it efficiently "repairs" the path by only re-calculating the portions that were affected by the change. This is much faster than re-planning from scratch and is a standard approach in robotics.

## Assessment for Module 3

### i. Convert the following natural language statements to first-order logic:

**Q: "All students who study hard will pass the exam"**

- **A (FOL):** `∀x (Student(x) ∧ StudiesHard(x)) → PassesExam(x)`
    
- **Explanation:**
    
    - We use the universal quantifier `∀x` ("for all x") because the statement is about "All students."
        
    - The implication `→` ("if...then") is the standard connective to use with `∀`.
        
    - The "if" part (antecedent) is that `x` is _both_ a `Student(x)` AND `StudiesHard(x)`.
        
    - The "then" part (consequent) is that `x` `PassesExam(x)`.
        

**Q: "There exists a student who is both smart and hardworking"**

- **A (FOL):** `∃x (Student(x) ∧ Smart(x) ∧ Hardworking(x))`
    
- **Explanation:**
    
    - We use the existential quantifier `∃x` ("there exists an x") because of the phrase "There exists."
        
    - The conjunction `∧` ("and") is the standard connective to use with `∃`.
        
    - We are asserting the existence of a single `x` that has all three properties at the same time: `Student(x)` AND `Smart(x)` AND `Hardworking(x)`.
        

**Q: "No lazy student passes without studying"**

- **A (FOL):** `∀x (Student(x) ∧ Lazy(x) ∧ ¬Studies(x)) → ¬Passes(x)`
    
- **Explanation:**
    
    - "No" is a universal quantifier that denies something. The easiest way to write this is "For all x, if x is a student AND is lazy AND does not study, THEN x does not pass."
        
    - `Student(x) ∧ Lazy(x) ∧ ¬Studies(x)` identifies the _exact_ type of person we are talking about (a lazy student who doesn't study).
        
    - `→ ¬Passes(x)` is the conclusion for this type of person (they do not pass).
        

### ii. Design a semantic network for the following domain:

**Q: "Transportation vehicles, including cars, trucks, boats, and airplanes. Cars and trucks are land vehicles, boats are water vehicles, and airplanes are air vehicles. All vehicles have engines and can transport people."**

- **A (Design):**
    
    ```
                      [Vehicle]
                         |
             /-----------+-----------\
             |           |           |
          (is_a)      (is_a)      (is_a)
             |           |           |
     [Land Vehicle] [Water Vehicle] [Air Vehicle]
          |           |           |
      /-------\       (is_a)      (is_a)
      |       |         |           |
    (is_a)  (is_a)    [Boat]    [Airplane]
      |       |
    [Car]   [Truck]
    ```
    
- **Attached Properties:**
    
    - `[Vehicle]` --(has_property)--> `[Engine]`
        
    - `[Vehicle]` --(can_do)--> `[Transport People]`
        
- **Explanation:** This network uses **inheritance** (the `is_a` links).
    
    1. We place the most general properties, `[Engine]` and `[Transport People]`, on the main `[Vehicle]` node.
        
    2. Because `[Land Vehicle]`, `[Water Vehicle]`, and `[Air Vehicle]` are all `(is_a)` `[Vehicle]`, they _inherit_ these properties.
        
    3. Furthermore, `[Car]` and `[Truck]` _inherit_ properties from `[Land Vehicle]`, which in turn inherits from `[Vehicle]`.
        
    4. This means that, by following the `is_a` links, our system knows that a `[Car]` has an `[Engine]` and can `[Transport People]` without us having to state those facts explicitly for every single vehicle type. This is very efficient.
        

### iii. Explain the differences between forward chaining and backward chaining inference. When would you use each?

|Feature|**Forward Chaining (Data-Driven)**|**Backward Chaining (Goal-Driven)**|
|---|---|---|
|**Starting Point**|**Facts** (Data)|**Goal** (Hypothesis / Query)|
|**Process**|1. Start with known facts.<br><br>2. Find rules where the `IF` part is matched by the facts.<br><br>3. "Fire" these rules, adding their `THEN` parts as _new facts_.<br><br>4. Repeat until no new facts can be derived.|1. Start with a goal (e.g., `?HasFlu(John)`).<br><br>2. Find rules where the `THEN` part matches the goal.<br><br>3. The `IF` parts of these rules become new _subgoals_.<br><br>4. Repeat, working backward until all subgoals are matched to known facts.|
|**Analogy**|"What new conclusions can we draw from the data we just received?"|"Can we prove this hypothesis is true? If so, what facts do we need?"|
|**Direction**|Facts → Conclusions|Goal → Subgoals → Facts|

**When to use each:**

- **Use Forward Chaining (Data-Driven) when:**
    
    - You are **monitoring** a situation and need to _react_ to new information (e.g., a stock market bot sees new prices (facts) and triggers a "buy" or "sell" rule).
        
    - You are **filtering** or classifying (e.g., an email system gets a new email (fact) and runs rules to classify it as "Spam," "Urgent," or "General").
        
    - You want to find _all possible_ conclusions from a set of starting facts.
        
- **Use Backward Chaining (Goal-Driven) when:**
    
    - You are building a **diagnostic** system (e.g., a medical expert system starting with the goal `?HasDisease(X)` and working backward to check symptoms).
        
    - You are building a **question-answering** system or a virtual assistant. The user's question is the "goal" you need to prove.
        
    - You have a clear hypothesis to test and don't want to waste time deriving thousands of unrelated conclusions.
        

### iv. List and explain three limitations of expert systems. How might modern AI approaches address these limitations?

1. **Limitation: Knowledge Acquisition Bottleneck**
    
    - **Explanation:** This is often the biggest problem. It is extremely difficult, time-consuming, and expensive to interview a human expert, extract their "rules of thumb," and manually code them into a formal `IF-THEN` rule base. The expert might not even be able to explain _how_ they know something—they just "know."
        
    - **Modern AI Solution: Machine Learning (ML).** Instead of manual programming, we use ML. We can feed a neural network 100,000 patient records (symptoms + final diagnoses). The model _learns_ the complex patterns and correlations on its own, effectively building its own "rules" from the data, bypassing the human interview process.
        
2. **Limitation: Brittleness (Narrow Domain)**
    
    - **Explanation:** Expert systems are "brittle," meaning they fail completely—like falling off a cliff—when faced with a problem even _slightly_ outside their narrow, pre-programmed domain. A car engine expert system knows nothing about transmissions, let alone bicycles. It has no "common sense" to fall back on.
        
    - **Modern AI Solution: Large Language Models (LLMs) & Deep Learning.** Modern models like LLMs are trained on massive, diverse datasets (like a large portion of the internet). This gives them a broad, general understanding of the world and a form of "common sense." They can handle a much wider variety of queries and topics and tend to "degrade gracefully" (give a less helpful answer) rather than crash when they encounter an unfamiliar topic.
        
3. **Limitation: Difficulty Handling Uncertainty**
    
    - **Explanation:** Traditional `IF-THEN` rules are very black and white (Boolean). `IF (has_fever) THEN...` This rule is either True or False. It's difficult to represent "maybe," "probably," or "70% likely." The real world is full of uncertainty, not true/false facts.
        
    - **Modern AI Solution: Probabilistic AI (e.g., Bayesian Networks) & ML.** Modern ML models are inherently probabilistic. A modern classifier doesn't just say, "That's a cat." It outputs a probability distribution: `(Cat: 95%, Dog: 4%, Rabbit: 1%)`. This ability to work with and output probabilities makes them far better at handling the "gray areas" and uncertainty of the real world.