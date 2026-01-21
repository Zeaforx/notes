 # MODULE 3: KNOWLEDGE REPRESENTATION AND REASONING

## Learning Objectives

By the end of this module, students should be able to:

- Understand different approaches to knowledge representation.
    
- Work with propositional logic and first-order logic.
    
- Implement knowledge bases and inference engines.
    
- Design semantic networks and frame-based systems.
    
- Apply logical reasoning to solve AI problems.
    
- Build simple expert systems using Python.
    
- Evaluate the trade-offs between different representation schemes.
    

## Module Structure

- **Theory Session:** Logic systems, knowledge representation schemes, reasoning methods.
    
- **Practical Lab:** Building knowledge bases, implementing inference engines, expert system development.
    

## THEORY SESSION

### 1. Introduction to Knowledge Representation

#### 1.1 What is Knowledge Representation?

Knowledge Representation (KR) is the field of AI concerned with representing information about the world in a form that a computer system can utilize to solve complex tasks. It's not just about storing data; it's about storing it in a way that allows the system to _reason_ with it.

**Key Questions:**

- How do we represent what we know about the world? (e.g., "The sky is blue," "All dogs are mammals.")
    
- How do we reason with this knowledge? (e.g., If "All dogs are mammals" and "Fido is a dog," how do we conclude "Fido is a mammal"?)
    
- How do we make inferences and draw new conclusions?
    



**Real-World Example:** A medical diagnosis chatbot.

- **Data:** A list of patient symptoms.
    
- **Knowledge:** A represented "knowledge base" (KB) that links symptoms to diseases (e.g., "Fever AND cough AND loss of smell" _strongly suggests_ "COVID-19").
    
- **Reasoning:** The chatbot uses an "inference engine" to compare the patient's data (symptoms) against its knowledge (the KB) to infer a probable diagnosis.*
    

#### 1.2 Requirements for Good Knowledge Representation

A good KR system should be:

1. **Representational Adequacy:** The ability to represent all the kinds of knowledge needed in the domain.
    
    - 
        
        Example: A system for a self-driving car must be able to represent roads, other cars, pedestrians, traffic light states (red, green, yellow), and the rules of driving.
        
2. **Inferential Adequacy:** The ability to derive new knowledge (inferences) from the existing knowledge.
    
    - 
        
        Example: If the KB knows "All humans are mortal" and "Socrates is a human," it must have a mechanism to _infer_ that "Socrates is mortal."
        
3. **Inferential Efficiency:** The ability to make inferences and derive new knowledge efficiently (i.e., quickly).
    
    - 
        
        This is critical for real-time systems. A self-driving car can't take 10 seconds to infer that a red light means "stop." The inference must be nearly instantaneous.
        
4. **Acquisitional Efficiency:** The ability to acquire new knowledge easily.
    
    - 
        
        How easily can the system be updated? Can it learn from a database, by reading text, or from user input? A system that requires a programmer to manually add every new fact is not very efficient.
        

#### 1.3 Types of Knowledge

- **Declarative Knowledge:** Facts about the world. "What" we know.
    
    - Example: "Birds can fly," "Tweety is a bird," "The capital of France is Paris."
        
- **Procedural Knowledge:** Knowledge of _how_ to do things. The "how-to" steps.
    
    - Example: Rules for driving, a cooking recipe, the steps to solve a quadratic equation.
        
- **Meta-Knowledge:** Knowledge _about_ knowledge.
    
    - Example: "John knows that Mary likes pizza." (This is knowledge about what John knows).
        
    - 
        
        Another example: "The rule 'All birds can fly' has exceptions." This meta-knowledge informs the system how to apply the "Birds can fly" rule.
        

### 2. Propositional Logic

Propositional Logic (or Propositional Calculus) is the simplest form of logic. It's a foundational system for understanding how reasoning works.

#### 2.1 Basic Components

- **Propositions:** Declarative statements that are either **True** or **False**. They are the "atoms" of this logic.
    
    - Example: `P` = "It is raining," `Q` = "The ground is wet."
        
    - _"My dog is cute"_ is not a good proposition because "cute" is subjective. _"My dog is a beagle"_ is a good proposition.
        
- **Logical Connectives:** Operators used to combine simple propositions into more complex sentences.
    
    - **Negation (NOT):** `¬P`
        
        - "It is **not** raining."
            
    - **Conjunction (AND):** `P ∧ Q`
        
        - "It is raining **AND** the ground is wet." (True only if _both_ are true)
            
    - **Disjunction (OR):** `P ∨ Q`
        
        - "It is raining **OR** the ground is wet." (True if _at least one_ is true)
            
    - **Implication (IF...THEN):** `P → Q`
        
        - "**If** it is raining, **then** the ground is wet." (This is an interesting one. It's only False if `P` is True and `Q` is False).
            
    - **Biconditional (IF AND ONLY IF):** `P ↔ Q`
        
        - "It is raining **if and only if** the ground is wet." (True only if `P` and `Q` have the _same_ truth value).
            

#### 2.2 Truth Tables

Truth tables are used to show the value of a complex sentence for all possible combinations of truth values of its propositions.

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
|**P**|**Q**|**¬P (not P)**|**P ∧ Q (P and Q)**|**P ∨ Q (P or Q)**|**P → Q (if P then Q)**|**P ↔ Q (P iff Q)**|
|T|T|F|T|T|T|T|
|T|F|F|F|T|F|F|
|F|T|T|F|T|T|F|
|F|F|T|F|F|T|T|

#### 2.3 Knowledge Base and Inference

- **Knowledge Base (KB):** A set of sentences in propositional logic that we know (or assume) to be true.
    
    - Example: `{P → Q, P, Q ∨ R}`
        
- **Inference:** The process of deriving new sentences (new knowledge) from the existing KB.
    
- **Common Inference Rules:** These are templates for valid reasoning.
    
    1. **Modus Ponens (Mode that Affirms):**
        
        - **Rule:** If we have `(P → Q)` and we have `P`, we can infer `Q`.
            
        - **Example:**
            
            1. KB has: "If it is raining (`P`), then the ground is wet (`Q`)." (`P → Q`)
                
            2. KB learns: "It is raining." (`P`)
                
            3. Inference: The system can conclude, "The ground is wet." (`Q`)
                
    2. **Modus Tollens (Mode that Denies):**
        
        - **Rule:** If we have `(P → Q)` and we have `¬Q`, we can infer `¬P`.
            
        - **Example:**
            
            1. KB has: "If it is raining (`P`), then the ground is wet (`Q`)." (`P → Q`)
                
            2. KB learns: "The ground is **not** wet." (`¬Q`)
                
            3. Inference: The system can conclude, "It is **not** raining." (`¬P`)
                
    3. **Resolution:**
        
        - **Rule:** `(P ∨ Q), (¬P ∨ R) ⊢ (Q ∨ R)`
            
        - **Explanation:** This is a powerful rule used by many automated theorem provers. It says: "We know `P` or `Q` is true, and we also know `(not P)` or `R` is true. Since `P` must be either true or false, one of `Q` or `R` _must_ be true."
            

#### 2.4 Limitations of Propositional Logic

Propositional logic is useful, but it's too simple for most real-world problems.

1. **Limited Expressiveness:** It cannot represent relationships between objects or generalize over them.
    
2. **No Quantification:** It cannot represent concepts like "All," "Every," or "Some."
    
3. **Not Scalable:** It's difficult to represent complex domains.
    


**Clear Example of Limitations:**

Consider the simple human statements:

1. "All students like AI."
    
2. "John is a student."
    

From this, a human can easily infer: "John likes AI."

**In propositional logic, this is impossible.**

- You would need a separate proposition for _every single student_:
    
    - `P1` = "John is a student."
        
    - `P2` = "John likes AI."
        
    - `P3` = "Jane is a student."
        
    - `P4` = "Jane likes AI."
        
    - ...and so on.
        
- There is no way to create a _single rule_ for "All students." You would have to create millions of rules: `(P1 → P2)`, `(P3 → P4)`, etc.
    

This inability to talk about _objects_ (like "John"), _properties_ (like "is a student"), and _quantifiers_ (like "All") is the main drawback of propositional logic and directly leads to the need for more expressive logics, like **First-Order Logic**.*

### 3. First-Order Logic (Predicate Logic)

First-Order Logic (FOL), or Predicate Logic, is a powerful upgrade from propositional logic. It allows us to represent knowledge about _objects_, their _properties_, and their _relations_.

#### 3.1 Enhanced Expressiveness

- **Objects:** Specific things in the world.
    
    - _Example:_ `John`, `Mary`, `Car1`, `KingJohnsCastle`
        
- **Properties:** Attributes that objects can have. These are represented by _predicates_ that take one object.
    
    - _Example:_ `Tall(John)`, `Red(Car1)`, `King(John)`
        
- **Relations:** Relationships between two or more objects. These are _predicates_ that take two or more objects.
    
    - _Example:_ `Loves(John, Mary)`, `Owns(Mary, Car1)`
        
- **Functions:** Mappings from one or more objects to another single object.
    
    - _Example:_ `FatherOf(John)` (maps John to his father), `Age(Mary)` (maps Mary to her age)
        

#### 3.2 Syntax Elements

- **Constants:** The specific objects.
    
    - _Example:_ `john`, `mary`, `car1`
        
- **Variables:** Stand-ins for arbitrary objects.
    
    - _Example:_ `x`, `y`, `z`
        
- **Predicates:** Represent properties or relations.
    
    - _Example:_ `Tall(x)`, `Loves(x, y)`, `Student(x)`
        
- **Functions:**
    
    - _Example:_ `FatherOf(x)`, `Age(x)`
        
- **Quantifiers:**
    
    - **Universal (∀ "for all"):** Makes a statement about _all_ objects.
        
        - `∀x Student(x) → Studies(x)`
            
        - **Translation:** "For all `x`, _if_ `x` is a Student, _then_ `x` Studies." (e.g., "All students study")
            
    - **Existential (∃ "there exists"):** Makes a statement about _at least one_ object.
        
        - `∃x Student(x) ∧ Smart(x)`
            
        - **Translation:** "There exists an `x` _such that_ `x` is a Student **AND** `x` is Smart." (e.g., "There exists a smart student")
            

#### 3.3 Example Representations

- **Natural Language:** "All birds can fly."
    
- **First-Order Logic:** `∀x Bird(x) → CanFly(x)`
    
- **Natural Language:** "Tweety is a bird. All birds can fly. Therefore, Tweety can fly."
    
- **Knowledge Base:**
    
    1. `Bird(tweety)` (Fact)
        
    2. `∀x Bird(x) → CanFly(x)` (Rule)
        
- **Inference:**
    
    - The system can apply the rule (2) to the fact (1) to infer a new fact: `CanFly(tweety)`.
        

#### 3.4 Inference in First-Order Logic

- **Unification:** The process of finding substitutions for variables to make two logical expressions identical. This is the pattern-matching engine that lets FOL reasoning work.
    
    - **Example:** We want to unify `Loves(john, x)` with the fact `Loves(john, mary)`.
        
    - **Result:** The unification succeeds by binding the variable `x` to the constant `mary` (i.e., `x = mary`).


Deeper look at inference methods:

- **Forward Chaining (Data-Driven Reasoning):**
    
    - **How it works:** Starts with the facts in the KB. It applies all rules whose premises (IF parts) are satisfied by those facts. This generates _new_ facts. These new facts are added to the KB, which in turn might trigger _more_ rules. This chain reaction continues until no new facts can be derived.
        
    - **Example:**
        
        1. **KB:** `HasFeathers(Condor)`, `LaysEggs(Condor)`, `∀x (HasFeathers(x) → Bird(x))`, `∀y (Bird(y) ∧ LaysEggs(y) → IsReproducing(y))`
            
        2. **Chain (Cycle 1):** The fact `HasFeathers(Condor)` matches the rule `∀x (HasFeathers(x) → Bird(x))`.
            
        3. **New Fact:** `Bird(Condor)` is generated and added to the KB.
            
        4. **Chain (Cycle 2):** The KB now has `Bird(Condor)` and `LaysEggs(Condor)`. These _together_ match the rule `∀y (Bird(y) ∧ LaysEggs(y) → IsReproducing(y))`.
            
        5. **New Fact:** `IsReproducing(Condor)` is generated.
            
    - **Real-World Use:** Good for monitoring or filtering systems. E.g., a stock market system where new facts (price changes) trigger rules (buy/sell alerts).
        
- **Backward Chaining (Goal-Driven Reasoning):**
    
    - **How it works:** Starts with a _goal_ (a query) and works backward. To prove the goal, it finds rules that _conclude_ that goal. It then tries to prove the premises (IF parts) of those rules. These premises become new _subgoals_, and the process repeats until it can match the subgoals against known facts.
        
    - **Example:**
        
        1. **KB:** Same as above.
            
        2. **Goal Query:** `?IsReproducing(Condor)`
            
        3. **Step 1:** System finds the rule `∀y (Bird(y) ∧ LaysEggs(y) → IsReproducing(y))`.
            
        4. **New Subgoals:** To prove the goal, it must prove (A) `?Bird(Condor)` and (B) `?LaysEggs(Condor)`.
            
        5. **Step 2 (for Subgoal A):** To prove `?Bird(Condor)`, it finds the rule `∀x (HasFeathers(x) → Bird(x))`.
            
        6. **New Subgoal:** It must prove `?HasFeathers(Condor)`.
            
        7. **Step 3 (for Subgoal A):** System finds `HasFeathers(Condor)` as a _fact_ in the KB. Subgoal `?HasFeathers(Condor)` is **TRUE**.
            
        8. **Step 4 (for Subgoal A):** Since `?HasFeathers(Condor)` is true, `?Bird(Condor)` is **TRUE**.
            
        9. **Step 5 (for Subgoal B):** System finds `LaysEggs(Condor)` as a _fact_ in the KB. Subgoal `?LaysEggs(Condor)` is **TRUE**.
            
        10. **Conclusion:** Since both Subgoal A (`Bird(Condor)`) and Subgoal B (`LaysEggs(Condor)`) are true, the original Goal `IsReproducing(Condor)` is **TRUE**.
            
    - **Real-World Use:** This is the core of diagnostic systems and question-answering. A medical expert system would use backward chaining to prove the goal `?HasDisease(Patient, "Flu")` by setting subgoals to check for symptoms.
        

### 4. Alternative Knowledge Representation Schemes

Logic is powerful, but not always the most natural or efficient way to represent knowledge.

#### 4.1 Semantic Networks

- **Structure:** A graph-based representation.
    
    - **Nodes:** Represent objects, concepts, or categories.
        
    - **Labeled Edges (Links):** Represent relationships between nodes.
        
- **Example:** A simple network:
    
    - `[Perry]` --(is_a)--> `[Bird]`
        
    - `[Bird]` --(is_a)--> `[Animal]`
        
    - `[Bird]` --(has_part)--> `[Wings]`
        
    - `[Bird]` --(can_do)--> `[Fly]`
        
    - `[Animal]` --(property)--> `[CanBreathe]`
		
		![[Pasted image 20260114145800.png]]
        
- **Key Feature: Inheritance.** Properties are inherited up the "is_a" chain. In the example, `Perry` _inherits_ the ability to `Fly` from `Bird`, and the property `CanBreathe` from `Animal`.
    
- **Advantages:**
    
    1. Natural representation of hierarchies and "is-a" relationships.
        
    2. Easy to visualize and understand.
        
    3. Supports inheritance, which is an efficient way to store properties.
        
- **Disadvantages:**
    
    1. **Informal Semantics:** The meaning of the links can be ambiguous. What does a "has" link _really_ mean? This makes automated reasoning difficult.
        
    2. **Limited Reasoning Capabilities:** Not as expressive as FOL. Difficult to represent quantification ("All," "Some") or complex logical statements.
        

#### 4.2 Frames

- **Structure:** A more structured, object-oriented approach. A "frame" is like a template for an object, containing "slots" (attributes) that are filled with "fillers" (values).
    
- **Example Frames:**
    

|                 |                             |
| --------------- | --------------------------- |
| **Frame: BIRD** |                             |
| `is_a`:         | `ANIMAL`                    |
| `has_parts`:    | `wings`, `feathers`, `beak` |
| `can`:          | (Default: `fly`, `sing`)    |
| `locomotion`:   | (Default: `flying`)         |

|   |   |
|---|---|
|**Frame: PERRY**||
|`is_a`:|`BIRD`|
|`color`:|`yellow`|
|`size`:|`small`|
|`can`:|`sing` (inherits `fly`)|

- **Key Features:**
    
    - **Inheritance:** `Perry` inherits all slots and fillers from its `is_a` parent, `BIRD`.
        
    - **Default Values:** Slots can have default values (e.g., `BIRD.can` defaults to `fly`). These can be overridden by a child frame (an "instance").
        
    - **Procedures (Attached Procedures):** A slot's value doesn't have to be static. It can be a procedure (a small piece of code) that runs when the value is needed.
        
        - $$Expanded$$
            
            Example: A `PERSON` frame might have a `birthdate` slot and an `age` slot. The `age` slot could contain an `if-needed` procedure that calculates `(CurrentDate - birthdate)`.
            

#### 4.3 Production Rules

- **Structure:** A set of `IF-THEN` rules (also called "productions"). This is one of the most common KR methods, especially for expert systems.
    
- **Components:**
    
    1. **Rule Base:** The set of all rules.
        
    2. **Working Memory:** The set of current facts.
        
- **Example:**
    
    - `Rule 1: IF (animal has feathers) THEN (animal is bird)`
        
    - `Rule 2: IF (animal is bird) AND (animal can fly) THEN (bird_type is flying-bird)`
        
    - `Rule 3: IF (animal is bird) AND (animal cannot fly) THEN (bird_type is flightless-bird)`
        
- **Advantages:**
    
    - **Natural Representation:** Very intuitive for representing human expertise, which is often in the form of "if this happens, then do that."
        
    - **Modular:** Rules are independent units. You can add, remove, or modify rules without rewriting the whole system.
        
    - **Explainable:** The system's reasoning process is easy to trace by simply listing the sequence of rules that fired.
        

### 5. Expert Systems

An expert system is an AI program designed to solve problems within a specialized domain, operating at the level of a human expert.

#### 5.1 Architecture

1. **Knowledge Base:** The "library" of the system.
    
    - Contains the domain-specific knowledge, typically stored as **production rules** and **facts**.
        
2. **Inference Engine:** The "brain" of the system.
    
    - An algorithm (like **Forward Chaining** or **Backward Chaining**) that applies the rules in the Knowledge Base to the facts in Working Memory to derive new conclusions.
        
3. **User Interface:** The system that allows a non-expert user to interact with the system, providing facts and asking questions.
    
4. **Explanation Facility:** A crucial component that explains the "how" and "why" of the system's reasoning process.
    
        Example: "I concluded `bird_type is flightless-bird` _BECAUSE_ you told me `animal is bird` (from Rule 1) and `animal cannot fly` (user fact), which triggered Rule 3."
        
5. **Working Memory:** A temporary database of facts about the _current_ problem being solved.
    

#### 5.2 Types of Expert Systems

- **Diagnostic Systems:** Infer the cause of a problem from symptoms.
    
    - _Example:_ Medical diagnosis (e.g., MYCIN for blood infections), fault detection in machinery.
        
- **Configuration Systems:** Help build a complex object from components, ensuring all constraints are met.
    
    - _Example:_ Configuring computer systems, planning factory layouts.
        
- **Monitoring Systems:** Observe system behavior and raise alarms when things go wrong.
    
    - _Example:_ Process monitoring in a power plant, patient monitoring in an ICU.
        
- **Planning Systems:** Develop a sequence of actions to achieve a goal.
    
    - _Example:_ Mission planning for NASA, scheduling for airlines.
        

#### 5.3 Advantages and Limitations

- **Advantages:**
    
    1. **Capture Human Expertise:** Can preserve and distribute the knowledge of a rare expert.
        
    2. **Consistent Performance:** Doesn't get tired, bored, or make emotional mistakes.
        
    3. **Available 24/7:** Can be used anywhere, anytime.
        
    4. **Easy to Replicate:** Once built, it can be copied and distributed cheaply.
        
- **Limitations:**
    
    1. **Narrow Domains:** An expert system for "car engines" knows _nothing_ about "car transmissions," let alone "bicycles."
        
    2. **Brittle:** Fails completely ("falls off a cliff") when it encounters a problem just slightly outside its domain. It has no "common sense."
        
    3. **Knowledge Acquisition Bottleneck:** This is the biggest challenge. Getting the knowledge out of a human expert's head and into a set of formal rules is extremely difficult, time-consuming, and expensive.
        
    4. **Difficulty Handling Uncertainty:** Basic expert systems struggle with "maybe" or "probably." (This led to extensions like fuzzy logic and Bayesian networks).
        

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
        
- Explanation:
    
    This network uses inheritance (the is_a links).
    
    1. We place the most general properties, `[Engine]` and `[Transport People]`, on the main `[Vehicle]` node.
        
    2. Because `[Land Vehicle]`, `[Water Vehicle]`, and `[Air Vehicle]` are all `(is_a)` `[Vehicle]`, they _inherit_ these properties.
        
    3. Furthermore, `[Car]` and `[Truck]` _inherit_ properties from `[Land Vehicle]`, which in turn inherits from `[Vehicle]`.
        
    4. This means that, by following the `is_a` links, our system knows that a `[Car]` has an `[Engine]` and can `[Transport People]` without us having to state those facts explicitly for every single vehicle type. This is very efficient.
        

### iii. Explain the differences between forward chaining and backward chaining inference. When would you use each?

|                    |                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Feature**        | **Forward Chaining (Data-Driven)**                                                                                                                                                                                                                     | **Backward Chaining (Goal-Driven)**                                                                                                                                                                                                                                                       |
| **Starting Point** | **Facts** (Data)                                                                                                                                                                                                                                       | **Goal** (Hypothesis / Query)                                                                                                                                                                                                                                                             |
| **Process**        | 1. Start with known facts.<br><br>  <br><br>2. Find rules where the `IF` part is matched by the facts.<br><br>  <br><br>3. "Fire" these rules, adding their `THEN` parts as _new facts_.<br><br>  <br><br>4. Repeat until no new facts can be derived. | 1. Start with a goal (e.g., `?HasFlu(John)`).<br><br>  <br><br>2. Find rules where the `THEN` part matches the goal.<br><br>  <br><br>3. The `IF` parts of these rules become new _subgoals_.<br><br>  <br><br>4. Repeat, working backward until all subgoals are matched to known facts. |
| **Analogy**        | "What new conclusions can we draw from the data we just received?"                                                                                                                                                                                     | "Can we prove this hypothesis is true? If so, what facts do we need?"                                                                                                                                                                                                                     |
| **Direction**      | Facts → Conclusions                                                                                                                                                                                                                                    | Goal → Subgoals → Facts                                                                                                                                                                                                                                                                   |

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