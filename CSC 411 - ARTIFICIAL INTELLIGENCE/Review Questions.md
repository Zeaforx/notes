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
	 
- **Data Bias:** The most common source. If the training data contains historical prejudices or lacks representation of certain groups, the AI will learn and replicate those patterns.
    
- **Algorithmic Bias:** Occurs when the mathematical model itself or its optimization goals inadvertently prioritize one outcome over another, even if the data is balanced.
    
- **Human/Cognitive Bias:** Developers and data scientists may unconsciously project their own life experiences and perspectives into how they define a "successful" outcome or choose which data points are important.
	 

**Differences:** Historical is about the _state of the world_, Representation is about _how we collect data_, and Algorithmic is about _how the model processes it_.

### 19. AI Bias: Definition, Types, and Impact

Bias in Artificial Intelligence (AI) refers to the phenomenon where a machine learning model produces results that are systematically prejudiced. These biases often reflect existing human prejudices or flaws in the data collection process, leading to "unfair" decisions that can marginalize specific demographics based on race, gender, age, or socioeconomic status.

### 20. The Bag of Words (BoW) Approach

BoW simply counts how many times each word appears. It creates a "frequency vector."

### Results for Doc 1:

|Word|Count|Importance (BoW)|
|---|---|---|
|**a**|2|**High**|
|**space**|2|**High**|
|explorer|1|Medium|
|travels|1|Medium|
|to|1|Medium|
|distant|1|Medium|
|planet|1|Medium|
|in|1|Medium|

**The Flaw:** In BoW, the word "**a**" is considered just as important as "**space**" because they both appear twice. The word "**travels**" is considered less important than "**a**."

#### 2. The TF-IDF Approach

TF-IDF applies a penalty to words that appear in many documents (Inverse Document Frequency).

### Calculation Logic:

1. **Term Frequency (TF):** How often is the word in _this_ document?
    
2. **Inverse Document Frequency (IDF):** How many documents in the _whole collection_ contain this word? If it's in every document, the weight drops to near zero.
    

### Results for Doc 1 (TF-IDF Weighted):

|Word|Frequency|Distribution|TF-IDF Score (Importance)|
|---|---|---|---|
|**a**|High|In all 3 docs|**Very Low** (Common filler)|
|**space**|High|In 2 of 3 docs|**Medium** (Topic indicator)|
|**explorer**|Medium|Only in 1 doc|**Very High** (Unique identifier)|
|**planet**|Medium|Only in 1 doc|**Very High** (Unique identifier)|
To illustrate the difference, let's assume we have a **Corpus** (collection) of three movie descriptions:

- **Doc 1:** "A space explorer travels to a distant planet in space."
    
- **Doc 2:** "A space station orbit is maintained by a space crew."
    
- **Doc 3:** "A romantic story about a chef in a small town."
	 
 - Comparison of Outcomes

	### Case A: The "Stop Word" Problem
	
	- **BoW:** Words like "the," "is," "a," and "of" usually have the highest scores. If you use BoW to find "similar" documents, a document about **cooking** and a document about **quantum physics** might look similar just because they both use the word "the" 50 times.
	    
	- **TF-IDF:** Automatically "muffles" these words. Because "the" appears in almost every document in the English language, its IDF score is nearly 0, effectively removing it from the calculation.
	    
	
	### Case B: Finding the "Essence"
	
	- **BoW:** If you have a 1,000-page book on **Biology**, the word "Biology" might appear 100 times, but the word "and" might appear 5,000 times. BoW thinks the book is about "and."
	    
	- **TF-IDF:** Recognizes that while "and" is frequent, it's frequent _everywhere_. However, the word "Biology" is frequent in _this_ book but rare in a collection of Cookbooks or History books. Therefore, "Biology" gets the highest score.
	    
	
	### Case C: Search Engines
	
	- **BoW:** If you search for "Space Explorer," BoW might show you any page that uses the word "the" or "a" frequently.
	    
	- **TF-IDF:** Will prioritize pages where "Space" and "Explorer" appear often _relative_ to how often they appear on the rest of the internet. This is why you get relevant results instead of just common English pages. 

### 21. How to choose a K in K-means Clustering
#### 1. The Elbow Method

This is the most common visual technique. It measures the **Within-Cluster Sum of Squares (WCSS)**, also known as **Inertia**.

- **How it works:** You run K-means for a range of values (e.g., k=1 to 10). For each k, you calculate the WCSS (the sum of squared distances between each point and its assigned center).
    
    +1
    
- **The "Elbow":** As k increases, WCSS naturally drops because clusters get smaller. You look for the point where the rate of decrease shifts from "sharp" to "shallow." This "bend" in the graph is the elbow.
    
    +1
    

---

#### 2. The Silhouette Method

While the Elbow method focuses on how tight clusters are, the Silhouette method looks at how well-separated they are.

- **The Silhouette Score:** It measures how similar an object is to its own cluster compared to other clusters. The score ranges from −1 to +1.
    
    +1
    
    - **Near +1:** The point is far away from neighboring clusters (good).
        
    - **Near 0:** The point is on or very close to the decision boundary between two clusters.
        
    - **Negative:** The point might have been assigned to the wrong cluster.
        
- **Choosing k:** You pick the k that yields the highest average silhouette score across all data points.
	
	
- The Formula
	
	For a single data point $i$, the silhouette score $s(i)$ is calculated as:
	
	$$s(i) = \frac{b(i) - a(i)}{\max\{a(i), b(i)\}}$$

- Breaking Down the Components

	To understand the result, we have to look at the two distances that make up the numerator:
	
	1. **$a(i)$ (Mean Intra-cluster Distance):** This is the average distance between point $i$ and all other points in the **same** cluster.
	    
	    - _Goal:_ You want this to be **small**, indicating that the point is very similar to its cluster-mates.
	        
	2. **$b(i)$ (Mean Nearest-cluster Distance):** This is the average distance between point $i$ and all points in the **nearest neighboring** cluster (the one it isn't part of, but is closest to).
	    
	    - _Goal:_ You want this to be **large**, indicating that the point is very different from points in other groups.
	        
