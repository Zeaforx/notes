# Week 7: HCI Evaluation: Criteria, Methods, and Selection

## I. Introductory Overview

In the field of Human-Computer Interaction (HCI), evaluation is the critical process of determining if a system is both **"easy to use"** and **"effective"** [i]. Without rigorous evaluation, designers cannot verify if their technical implementations meet the actual needs and cognitive constraints of users.

**The Analogy:** Evaluation is like a pilot performing a pre-flight checklist. You might have built a powerful engine (the backend), but if the cockpit controls (the UI) are confusing, the plane won't reach its destination safely.

## II. 1. Evaluation Criteria: The Five Usability Pillars

To measure "good usability," we break it down into five measurable pillars [i]:

- **Efficiency:** The speed at which a user can complete tasks once they have learned the system [i].
    
    - **Advanced Insight:** We can measure this quantitatively using **Fitts’ Law**, which predicts movement time based on target distance and width ($T = a + b \log_2(1 + D/W)$) [v]. Alternatively, **GOMS/KLM** (Goals, Operators, Methods, Selection rules) allows us to predict execution time by summing up the time taken for mental and physical operators, such as "P" for pointing or "M" for mental preparation [iii, iv].
        
- **Learnability:** The ease with which new users can accomplish basic tasks upon their first encounter [i].
    
    - **Advanced Insight:** **Linguistic Models** explain that learnability is high when the interaction language (syntax and semantics) is consistent [v]. If a system uses familiar terms like "Trash" instead of "Object Deletion Cache," the cognitive load is reduced because the system's "language" matches the user's real-world vocabulary [v].
        
- **Memorability:** The ability of casual users to return to a system after a period of non-use and still be able to operate it without re-learning everything [i].
    
- **Errors:** The frequency and severity of mistakes made by users, and how effectively the system helps them recover [ii].
    
- **Satisfaction:** The subjective "likability" and aesthetic appeal of the interface, often measured via the **System Usability Scale (SUS)** [ii].
    

**The Analogy:** Think of a rental car. **Learnability** is how quickly you find the lights; **Efficiency** is how fast you can adjust the mirrors once you know where the buttons are; **Memorability** is being able to drive it again after a week at the beach.

## III. 2. Evaluation through Expert Analysis (Inspection)

Expert analysis involves usability specialists examining an interface without involving real users. It is fast and identifies obvious flaws early [ii].

- **Heuristic Evaluation:** Experts check the interface against established "rules of thumb" (e.g., Nielsen’s 10 Heuristics) [ii].
    
    - **Analogy:** This is like a **building inspector** checking a house against the local code before anyone moves in. They don't need to live there to know if the wiring is a fire hazard [ii].
        
- **Cognitive Walkthrough:** Experts simulate a user’s thought process for specific tasks, checking if the system's guidance is obvious at every step [ii].
    
- **Pluralistic Walkthrough:** A collaborative "step-through" involving experts, users, and developers to ensure technical capabilities align with user expectations [ii].
    

**Design Principle vs. Usability Heuristic:**

- **Design Principle:** The **"Why"** (e.g., "Consistency reduces cognitive load") [i].
    
- **Usability Heuristic:** The **"Measurable Test"** (e.g., "Are the labels consistent across all screens?") [i].
    

## IV. 3. Evaluation through User Participation (Testing)

Testing with real users provides the most valid data on actual behavior but requires more resources [ii].

- **Usability Testing:** Users perform predefined tasks in a controlled setting while being timed and observed [ii].
    
- **Think-Aloud Protocol:** Users verbalize their thoughts and intentions continuously while working. This reveals the user's **mental model** and hidden frustrations [iii].
    
- **Field Studies:** Observing users in their actual environment (e.g., a nurse in a hospital) to capture real-world distractions and workflow interruptions [iii].
    
- **Questionnaires (SUS):** Gathering subjective data through standardized scales [iii].
    

Advanced Insight:

Before testing with humans, researchers can use Cognitive Architectures (like ACT-R) to simulate a synthetic user's thought process [v]. By running these simulations, designers can predict learning barriers and potential errors (e.g., if a label like "Forge" is used instead of "Create") before any code is even written [v].

## V. 4. Choosing an Evaluation Method

The selection depends on the design's maturity and available resources [iii].

|   |   |   |
|---|---|---|
|**Factor**|**Early/Conceptual Stage**|**Later/Refined Stage**|
|**Goal**|Find major problems; generate ideas|Validate performance; measure metrics|
|**Design Status**|Paper sketches; low-fidelity prototypes|High-fidelity prototypes; full system|
|**Resources**|Limited time and budget|Sufficient time; dedicated lab/budget|
|**Method**|**Expert Analysis** (Heuristic, Cognitive)|**User Testing** (Usability Tests, Field Studies)|

**The Analogy:** You use a **sketch** (Expert Analysis) to decide where the rooms go in a house, but you need a **walkthrough** (User Testing) to see if the hallways feel too narrow when you're carrying groceries.

## VI. Key Takeaway

**Strategic Timing:** Use **expert analysis** early and often to catch structural flaws cheaply. Use **user testing** later to confirm that the refined design actually works for the target audience in the real world [iii].

## VII. Illustrative Scenarios

### 1. Fitness Tracking App (Criteria Mapping)

- **Efficiency:** How long does it take to log a run after the process starts? [iii]
    
- **Learnability:** Can a first-time user track a walk without a tutorial? [iv]
    
- **Memorability:** Can a user find their history after a week of inactivity? [iv]
    

### 2. Smart Thermostat (Method Justification)

**Recommended:** **User Participation**. Because thermostats involve new mental models and are used in "low-attention" domestic environments (e.g., arriving home with groceries), only real users can reveal if the design is truly intuitive or if the "clicking" sound is annoying [iv].

### 3. University Portal (Heuristic Violation)

- **Violation:** A link buried three layers deep violates **Visibility of System Status** and **Recognition rather than Recall** [iv].
    
- **Violation:** A form that clears all data after a submission error violates **Error Prevention** and **Help Users Recognize/Recover from Errors** [iv].
    

### 4. Microwave Interface (Think-Aloud Pros/Cons)

- **Scenario:** A user says, "I pressed 'Popcorn', but it didn't start. Do I have to press 'Start' too?" [v]
    
- **Pro:** It reveals "hidden intentions" and identifies if the user's mental model matches the system logic [v].
    
- **Con:** It creates an **artificial environment**; the focus required to talk aloud might make the task seem easier or harder than it is during normal multi-tasking (e.g., cooking while talking) [v].
    

_Citations based on Course Week 7: HCI Evaluation: Criteria, Methods, and Selection [i-v]._

# HCI Models and Theories: A Deep Dive

## I. Introductory Overview

**HCI models and theories** serve as the foundational blueprint for designing **usable** and **efficient** interfaces. Rather than relying on guesswork, these frameworks provide computer scientists with analytical tools to predict how users will interact with a system, identify potential points of friction, and optimize the overall experience before development even begins.

## II. 1. Goal and Task Hierarchy Models

**Goal and Task Hierarchy Models** are analytical tools used to describe and predict user behavior by breaking down complex tasks into a structured hierarchy of objectives and actions.

- Definition & Components (GOMS Model):
    
    The GOMS framework describes user knowledge through four components:
    
    - **Goals:** What the user intends to achieve (e.g., "Send a text message").
        
    - **Operations:** Elementary, non-decomposable acts (e.g., "Press a key," "Move mouse").
        
    - **Methods:** Learned, step-by-step sequences of operations to achieve a goal.
        
    - **Selection Rules:** Logic used to choose between multiple available methods.
        
- **Application:**
    
    - **Predict Performance Time (KLM):** Assigning standardized times to operators to estimate task duration.
        
    - **Identify Bottlenecks:** Pinpointing cognitively demanding or slow steps in a workflow.
        
    - **Optimize Task Flow:** Guiding the creation of the most efficient paths for primary user goals.
        
- **Scenario 1:** A **KLM analysis** for sending a text to "Alex" involves calculating the time for **Mental Preparation (M)**, **Pointing (P)**, and **Keystrokes (K)**. By summing these (e.g., $T = T_M + T_P + 4 \times T_K...$), designers can compare this method against others, like using a home screen widget, to find the fastest design.
    
- Analogy:
    
    Think of GOMS as a detailed recipe. The "Goal" is the finished meal; "Operations" are the basic actions like chopping or stirring; "Methods" are the specific steps of the recipe; and "Selection Rules" tell you whether to use the oven or the microwave based on how much time you have.
    

## III. 2. Linguistic Models

**Linguistic models** view the interaction between a human and a computer as a conversation, focusing on the "language" used to communicate commands and intentions.

- **Definition & Key Concepts:**
    
    - **Interaction Language:** The set of commands, symbols, and layout rules used to communicate.
        
    - **Semantics:** The underlying meaning or effect of a command (e.g., "Save" means committing data to storage).
        
    - **Syntax:** The structure or sequence of the command (e.g., "Delete [File-name]").
        
- **Application:**
    
    - **Consistency:** Ensuring a command performs the same action everywhere to reduce cognitive load.
        
    - **Learnability:** Using intuitive terms that match real-world understanding.
        
    - **Error Prevention:** Avoiding ambiguous structures that lead to user confusion.
        
- Scenario 2:
    
    In academic statistical software, changing technical jargon like "Ingest Binary Blob" to "Import Project File" and "Execute Non-Deterministic Routine" to "Run Simulation" improves the "linguistics." Mapping to the user's vocabulary makes the software feel familiar rather than like a foreign language.
    
- Analogy:
    
    An interface is like a foreign language. If the "grammar" (syntax) is logical and the words (semantics) sound like words you already know, you can become fluent quickly. If the language keeps changing its rules, you’ll constantly make mistakes.
    

## IV. 3. Physical and Device Models

These models focus on the motor aspects of interaction—specifically how the physical design of hardware and software impact the speed and accuracy of user movements.

- Definition (Fitts' Law):
    
    Fitts' Law predicts the time ($T$) required to move to a target based on Distance (D) and Width (W):
    
    $T = a + b \log_2(1 + D/W)$
    
- **Design Principles:**
    
    1. **Large Targets are Faster:** Increasing width ($W$) decreases the index of difficulty.
        
    2. **Close Targets are Faster:** Decreasing distance ($D$) minimizes travel time.
        
    3. **"Edge-of-Screen" Advantage:** Targets at the edges are effectively infinitely large because the cursor cannot overshoot them.
        
- Scenario 3:
    
    A large "Send" button at the bottom of a mobile screen is highly efficient because it is close to the user’s thumb (low $D$) and has a large target area (high $W$). A small button in the top corner requires a long stretch ($D$) and precise aim (small $W$), making it significantly slower.
    
- Analogy:
    
    It's like throwing a dart. It is much easier and faster to hit a giant dartboard (Large Target) that is standing right in front of you (Close Target) than it is to hit a tiny bullseye on the other side of the room.
    

## V. 4. Cognitive Architectures

**Cognitive Architectures** are integrated theories of the human mind used to create computational simulations of user behavior.

- Definition & Purpose:
    
    They enable Cognitive Modelling by creating "synthetic users" to perform "What-if" Analyses. Designers can simulate how a human would learn or fail at an interface before building a single line of code.
    
- ACT-R (Adaptive Control of Thought—Rational):
    
    A model that uses production rules (if-then statements) and procedural memory to simulate how users retrieve information and solve problems.
    
- Scenario 4:
    
    When simulating a user learning new software, an ACT-R model might attempt a general rule like "Look for a File menu." If the designer used a label like "Forge" instead of "Create," the simulation would show the "user" failing to match rules, leading to high cognitive load and error rates. This flags "Forge" as a major learnability barrier.
    
- Analogy:
    
    A Cognitive Architecture is like a flight simulator for the human brain. Instead of crashing a real plane (or frustrating real users), you test the "pilot's" reactions in a safe, simulated environment to see where they get confused.