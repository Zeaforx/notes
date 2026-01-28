# Introduction to Artificial Intelligence (CSC 411) - Test Solutions

## 1a) Define the following terms used in Artificial Intelligence:

- **i. Artificial Intelligence (AI):** The simulation of human intelligence processes by machines, especially computer systems. These processes include learning, reasoning, and self-correction.
    
- **ii. Machine Learning (ML):** A subset of AI that involves training algorithms to learn patterns from data and make predictions or decisions without being explicitly programmed for every specific rule.
    
- **iii. Confusion Matrix:** A table used to evaluate the performance of a classification model. It summarizes the correct and incorrect predictions with count values broken down by each class (True Positives, False Positives, True Negatives, False Negatives).
    
- **iv. Unsupervised Learning:** A type of machine learning where the algorithm is given data without explicit instructions on what to do with it (unlabeled data). The system tries to learn the patterns and structure from the data itself (e.g., clustering).
    
- **v. Mean Average Error:** (Likely refers to Mean Absolute Error - MAE). It is a metric used to evaluate regression models. It measures the average magnitude of the errors in a set of predictions, without considering their direction (calculated as the average of absolute differences between predicted and actual values).
    
- **vi. Algorithmic Bias:** Systematic and repeatable errors in a computer system that create unfair outcomes, such as privileging one arbitrary group of users over others, often stemming from biased training data.
    
- **vii. False Negative:** An error in binary classification where a test result indicates that a condition does not hold (negative), while in reality, it does (positive). (e.g., a sick patient diagnosed as healthy).
    
- **viii. False Positive:** An error in data reporting in which a test result improperly indicates the presence of a condition (positive), when in reality it is not present (negative). (e.g., a healthy patient diagnosed as sick).
    

## 1b) Compare and contrast the following AI concepts:

**i. Weak AI vs. Strong AI**

- **Weak AI (Narrow AI):** Designed and trained for a particular task. It operates within a limited context and simulates intelligence.
    
    - _Example 1:_ Apple's Siri or Amazon's Alexa.
        
    - _Example 2:_ Chess-playing algorithms (like Deep Blue).
        
- **Strong AI (General AI):** An AI system with generalized human cognitive abilities. It can find a solution when presented with an unfamiliar task and possesses consciousness/sentience (theoretical at this stage).
    
    - _Example 1:_ Data from Star Trek.
        
    - _Example 2:_ The T-800 from The Terminator (fictional).
        

**ii. Supervised Learning vs. Unsupervised Learning**

- **Supervised Learning:** The model learns from labeled training data (input-output pairs). Ideally, the model produces a function that maps inputs to desired outputs.
    
    - _Application:_ Email Spam Filtering (classifying emails as 'Spam' or 'Not Spam').
        
- **Unsupervised Learning:** The model learns from unlabeled data. It looks for previously undetected patterns in a data set with no pre-existing labels.
    
    - _Application:_ Customer Segmentation in marketing (clustering customers based on purchasing behavior).
        

## 1c) Briefly explain the following AI challenges and provide one solution for each:

**i. The knowledge acquisition bottleneck in expert systems**

- **Challenge:** The difficulty in extracting knowledge from human experts and converting it into a structured format (rules) that a computer can use.
    
- **Solution:** Using Machine Learning to mine patterns from data databases automatically, rather than relying solely on manual interviews with experts.
    

**ii. Overfitting in machine learning models**

- **Challenge:** When a model learns the training data too well, including the noise and outliers, leading to poor performance on new, unseen data.
    
- **Solution:** Regularization (adding a penalty for complexity) or Cross-validation.
    

**iii. Algorithmic bias in AI systems**

- **Challenge:** AI systems producing prejudiced results due to erroneous assumptions in the machine learning process or prejudiced training data.
    
- **Solution:** Using diverse and representative datasets for training and implementing "fairness metrics" to test models before deployment.
    

## 2a) The A* Search Algorithm

**i. Formula and Components**

The evaluation function formula is:

  

$$f(n) = g(n) + h(n)$$

- $f(n)$: The estimated total cost of the cheapest solution through node $n$.
    
- $g(n)$: The cost to reach node $n$ from the start node.
    
- $h(n)$: The heuristic function; the estimated cost from node $n$ to the goal.
    

**ii. Admissible Heuristic**

- **Explanation:** A heuristic is "admissible" if it never overestimates the cost to reach the goal. It is optimistic.
    
- **Importance:** Admissibility guarantees **optimality**. If the heuristic is admissible (and consistent), A* is guaranteed to return the shortest path (least cost) to the goal.
    

__iii. $A^*$  vs. Breadth-First Search (BFS)

- __Advantages of $A^*$ over BFS:_*
    
    1. **Efficiency:** A* is generally much faster because it uses a heuristic to guide the search toward the goal, whereas BFS expands blindly in all directions.
        
    2. **Focus:** A* expands fewer nodes to find the solution (if a good heuristic is used), reducing the search space.
        
- __Limitation of $A^*$ compared to BFS:
    
    1. **Complexity/Overhead:** A* requires the calculation of a heuristic function for every node, which adds computational overhead. Additionally, finding a good heuristic can be difficult. (Note: Both use significant memory, but A* is dependent on the heuristic quality).
        

## 2b) Propositional Logic vs. First-Order Logic

- **Distinction:** Propositional logic deals with simple declarative propositions (facts) that are either true or false. First-Order Logic (FOL) is more expressive; it includes objects, relations (predicates), and quantifiers (Universal $\forall$ and Existential $\exists$).
    
- **Example where FOL is more expressive:**
    
    - _Propositional Logic:_ You would need separate statements for every instance: `SocratesIsMortal`, `PlatoIsMortal`, `AristotleIsMortal`.
        
    - _FOL:_ You can express the general rule "All men are mortal" concisely: $\forall x (\text{Man}(x) \rightarrow \text{Mortal}(x))$.
        

## 2c) Forward Chaining Inference

**Knowledge Base:**

1. $\forall x (\text{Bird}(x) \rightarrow \text{CanFly}(x))$  
    
2. $\text{Bird}(\text{Tweety})$  
    
3. $\forall x (\text{Penguin}(x) \rightarrow \text{Bird}(x))$  
    
4. $\forall x (\text{Penguin}(x) \rightarrow \neg \text{CanFly}(x))$  
    

**Goal:** Conclude `CanFly(tweety)`?

**Steps:**

1. The inference engine looks at the known facts. We know `Bird(Tweety)`.
    
2. The engine searches for rules where the premise (IF part) matches the known facts.
    
3. Rule 1 states: "For all x, if x is a Bird, then x CanFly".
    
4. We substitute `Tweety` for `x`. Since `Bird(Tweety)` is true, the rule triggers.
    
5. **Conclusion:** We derive `CanFly(Tweety)`.
    
    - _(Note: While real-world penguins don't fly, the specific facts given about Tweety only identify him as a Bird, not a Penguin, so the logic holds)._
        

## 2d) Decision Trees

**i. How a decision tree makes predictions:**

A decision tree makes predictions by traversing from the root node down to a leaf node. At each internal node, it tests a specific attribute of the data. Based on the result of the test, it follows the corresponding branch. This process repeats until a leaf node is reached, which contains the final predicted class or value.

**ii. Calculate Gini Impurity**

- **Class Distribution:**
    
    - Class A: 60 samples
        
    - Class B: 30 samples
        
    - Class C: 10 samples
        
    - **Total Samples:** $60 + 30 + 10 = 100$  
        
- **Probabilities (**$p_i$**):**
    
    - $P(A) = 60/100 = 0.6$  
        
    - $P(B) = 30/100 = 0.3$  
        
    - $P(C) = 10/100 = 0.1$  
        
- **Formula:** $Gini = 1 - \sum (p_i)^2$  
    
- **Calculation:**
    
    - $P(A)^2 = 0.6^2 = 0.36$  
        
    - $P(B)^2 = 0.3^2 = 0.09$  
        
    - $P(C)^2 = 0.1^2 = 0.01$  
        
    - $\sum (p_i)^2 = 0.36 + 0.09 + 0.01 = 0.46$  
        
    - $Gini = 1 - 0.46 = \mathbf{0.54}$  
        

**iii. Two methods to prevent overfitting in decision trees:**

1. **Pruning:** Removing branches that use features with low importance (Pre-pruning or Post-pruning).
    
2. **Setting a Maximum Depth:** Limiting how deep the tree can grow to prevent it from memorizing specific training samples.
    

## 3a) Semantic Network

**Domain:** "Transportation vehicles, including cars, trucks, boats, and airplanes. Cars and trucks are land vehicles, boats are water vehicles, and airplanes are air vehicles. All vehicles have engines and can transport people."

**Nodes and Structure:**

- **Superclass:** Transportation Vehicle
    
- **Subclasses:** Land Vehicle, Water Vehicle, Air Vehicle
    
- **Instances/Specifics:** Car, Truck, Boat, Airplane
    
- **Properties:** Engine, People
    

**Relationships:**

1. **Transportation Vehicle** --(has part)--> **Engine**
    
2. **Transportation Vehicle** --(can transport)--> **People**
    
3. **Land Vehicle** --(is a)--> **Transportation Vehicle**
    
4. **Water Vehicle** --(is a)--> **Transportation Vehicle**
    
5. **Air Vehicle** --(is a)--> **Transportation Vehicle**
    
6. **Car** --(is a)--> **Land Vehicle**
    
7. **Truck** --(is a)--> **Land Vehicle**
    
8. **Boat** --(is a)--> **Water Vehicle**
    
9. **Airplane** --(is a)--> **Air Vehicle**
    

_(In a semantic network diagram, "Transportation Vehicle" would be at the top. It would have property links to "Engine" and "People". The specific vehicle types would inherit these properties through the "is a" links.)_

## 3b) Convert to First-Order Logic

**i. "Every person who buys policy is smart"**

- Definitions: $P(x)$: x is a person, $B(x)$: x buys policy, $S(x)$: x is smart.
    
- **Logic:** $\forall x ((P(x) \land B(x)) \rightarrow S(x))$  
    

**ii. "Not all students like both mathematics and Science"**

- Definitions: $S(x)$: x is a student, $L(x, y)$: x likes y.
    
- **Logic:** $\neg \forall x (S(x) \rightarrow (L(x, \text{Math}) \land L(x, \text{Science})))$  
    
- _Alternative (Equivalent):_ $\exists x (S(x) \land \neg (L(x, \text{Math}) \land L(x, \text{Science})))$