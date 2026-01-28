### 1. Propositional Logic vs. First Order Logic

- **Propositional Logic (PL):** Deals with propositions which are statements that are either true or false. It uses operators like AND, OR, NOT. It cannot see "inside" the statements.
    
    - _Example:_ "It is raining" (P) AND "The ground is wet" (Q).
        
- **First Order Logic (FOL):** An extension of PL that adds **predicates** and **quantifiers** (For all ∀, There exists ∃). It allows you to express relationships between objects.
    
    - _Example:_ "For all x, if x is a man, then x is mortal." (∀x(Man(x)→Mortal(x))).
        

### 2. Truth Table for Implication (P→Q)

The image shows a partial table. Here is the completed truth table for "If P, then Q":

|P|Q|P→Q|
|---|---|---|
|**T**|**T**|**T**|
|**T**|**F**|**F**|
|**F**|**T**|**T**|
|**F**|**F**|**T**|

Export to Sheets

### 3. Advantages of an Expert System

1. **Consistency:** Unlike humans, expert systems provide consistent answers for the same input and do not get tired or emotional.
    
2. **Preservation of Expertise:** They capture and preserve the knowledge of human experts, preventing knowledge loss if the expert leaves or retires.
    

### 4. Splitting Datasets (Training, Testing, Validation)

- **Training Set:** Used to train the model so it can learn patterns (weights and biases).
    
- **Validation Set:** Used during training to tune hyperparameters and prevent overfitting (allows you to check performance on data the model hasn't learned from directly).
    
- **Testing Set:** Used only _after_ the model is fully built to provide an unbiased evaluation of its final performance.
    

### 5. Decision Trees

- **How they make predictions:** A decision tree splits data into branches based on feature values. It starts at a "root" node and asks a series of questions (e.g., "Is Age > 30?"). Each answer leads to a new branch until a "leaf" node is reached, which contains the final prediction.
    
- **Three methods to prevent overfitting:**
    
    1. **Pruning:** Removing branches that provide little predictive power (can be pre-pruning or post-pruning).
        
    2. **Limiting Tree Depth:** Setting a maximum depth so the tree doesn't grow too complex.
        
    3. **Minimum Samples per Leaf:** Requiring a minimum number of data points to create a new leaf node.
        

### 6. High Bias and Low Variance

- **High Bias (Underfitting):** The model is too simple and misses the relations between features and target outputs (e.g., using a straight line to model a curve).
    
- **Low Variance:** The model is stable; small changes in the training data don't cause massive changes in the model structure.
    
- _Ideally, you want Low Bias and Low Variance, but there is often a trade-off._
    

### 7. Challenges in NLP

1. **Ambiguity:** Words often have multiple meanings depending on context (e.g., "bank" of a river vs. "bank" for money).
    
2. **Sarcasm and Irony:** Computers struggle to detect meaning when the literal words are the opposite of the intended sentiment.
    
3. **Slang and Idioms:** Informal language or cultural expressions ("break a leg") are difficult to translate literally.
    

### 8. NLP Definitions

- **Stemming:** The process of reducing a word to its base or root form (e.g., "running" → "run"). It is often a crude heuristic process.
    
- **Tokenization:** Breaking a stream of text into smaller units called tokens (words, characters, or subwords).
    
- **Stop Word Remover:** Filtering out common words that carry little unique meaning (e.g., "the", "is", "at") to focus on important keywords.
    

### 9. Why is text preprocessing essential?

Raw text is messy and unstructured. Preprocessing is essential to:

- Remove noise (punctuation, special characters).
    
- Reduce dimensionality (handling fewer unique words makes computation faster).
    
- Standardize inputs so the algorithm can process them effectively.
    

### 10. AI Concepts

- **Definitions:**
    
    - **AI (Artificial Intelligence):** The broad field of creating systems capable of performing tasks that typically require human intelligence.
        
    - **ML (Machine Learning):** A subset of AI where computers learn from data without being explicitly programmed for specific rules.
        
    - **NLP (Natural Language Processing):** The interaction between computers and human language.
        
    - **Neural Networks:** Computing systems inspired by biological brains, composed of layers of nodes.
        
- **Types of AI:**
    
    1. **Narrow AI (Weak AI):** Designed for a specific task (e.g., Siri, Chess bots). _Real-life example: Google Maps._
        
    2. **General AI (Strong AI):** Hypothetical AI with human-level cognitive abilities across widely varied tasks. _Real-life example: None exist yet (seen in sci-fi)._
        

### 11. Types of Learning

- **Supervised Learning:** The model learns from labeled training data (Input-Output pairs). _Example: Spam email classification._
    
- **Unsupervised Learning:** The model finds patterns in unlabeled data. _Example: Customer segmentation (clustering)._
    
- **Semi-Supervised Learning:** Uses a small amount of labeled data and a large amount of unlabeled data. _Example: Web page classification._
    
- **Reinforcement Learning:** An agent learns to make decisions by performing actions and receiving rewards or penalties. _Example: AlphaGo learning to play Go._
    

### 12. Algorithmic Bias

This occurs when an AI system reflects the values of the humans who created it or the data it was trained on, leading to unfair outcomes. _Example: A hiring AI favoring male resumes because it was trained on historical data where most hires were men._

### 13. Search Algorithms

- **Most Efficient:** **A* (A-Star) Search** is generally the most efficient because it uses a heuristic (h(n)) to estimate the cost to the goal, guiding the search intelligently.
    
- **BFS (Breadth-First Search):** Explores all neighbor nodes at the present depth before moving to nodes at the next depth level.
    
    - _Advantage:_ Guarantees the shortest path in unweighted graphs.
        
    - _Limitation:_ Uses a lot of memory (high space complexity).
        
- **A* vs BFS:** BFS is "blind" (explores everywhere evenly), while A* is "informed" (moves toward the goal).
    

### 13. (Second #13 in note) Knowledge Representation

- **Forward Chaining:** A reasoning method that starts with the available data (facts) and applies inference rules to extract more data until a goal is reached. (Data-driven).
    

### 14. Gini Impurity

A metric used in Decision Trees (specifically CART) to determine how to split data. It measures the likelihood of an incorrect classification of a new instance of a random variable. A Gini of 0 means pure (all items belong to one class).

### 15. Bag of Words (BoW)

A simplified representation used in NLP. It represents text as a "bag" (multiset) of its words, disregarding grammar and word order but keeping track of frequency (how many times a word appears).

### 16. Full Meaning of TF-IDF

**Term Frequency - Inverse Document Frequency.**

### 17. Advantages of TF-IDF over Bag of Words

- **Bag of Words** only counts frequency. It treats common words like "the" as very important because they appear often.
    
- **TF-IDF** balances this. It gives high weight to words that appear often in a specific document but rarely across the whole corpus. This helps identify the _unique_ and _relevant_ topics of a specific document.
    

### 18. Types of Bias

- **Historical Bias:** Bias that exists in the world (socio-cultural prejudices) and has seeped into the data generation process. (e.g., historical stereotypes).
    
- **Representation Bias:** Occurs when the training dataset does not well represent the population it is meant to serve (e.g., a face recognition dataset containing mostly light-skinned faces).
    
- **Algorithmic Bias:** Bias introduced by the algorithm itself or its optimization objective, often amplifying existing biases in the data.
    

**Differences:** Historical is about the _state of the world_, Representation is about _how we collect data_, and Algorithmic is about _how the model processes it_.