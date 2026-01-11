# CSC 441: Human-Computer Interaction (HCI) - Suggested Solutions

Air Force Institute of Technology

First Semester Examination 2024/2025

## Question 1 (25 Marks)

a. Mention the four key features of WIMP interface and their functions. (8 marks)

The four key features of a WIMP interface are:

1. **Windows:** Areas of the screen that behave as independent terminals for an application. They can usually contain text or graphics and can be moved or resized. They allow multiple activities to be visible simultaneously.
    
2. **Icons:** Small pictures or symbols used to represent applications, files, directories, or commands. They allow the user to interact with objects via "recognition" rather than "recall."
    
3. **Menus:** Lists of operations or commands that the system can perform. They allow users to scan available options and select one, reducing the need to memorize commands.
    
4. **Pointers:** An onscreen component (usually an arrow) controlled by an input device (mouse, trackpad). It allows the user to select, manipulate, and interact with the other three elements (Windows, Icons, Menus).
    

**b. Give two main differences between Toolbar and Menus. (2 marks)**

1. **Visibility/Access:** Toolbars are usually always visible and offer one-click access to frequently used commands. Menus are often hidden (collapsed) and require navigation (clicking to open) to access commands.
    
2. **Representation:** Toolbars primarily use iconic representations (sometimes with tooltips), while Menus primarily use text-based lists (though they may include icons).
    

**c. What are the types of Buttons that are commonly found in GUI of Computer and their functions? (5 marks)**

- **Radio Buttons:** Used for mutually exclusive choices (selecting one option automatically deselects the others in the group).
    
- **Checkboxes:** Used for non-exclusive choices (multiple options can be selected independently).
    
- **Push Buttons (Command Buttons):** Rectangular buttons (e.g., "OK", "Cancel", "Submit") that initiate a specific action or command immediately when clicked.
    

**d. Explain the functions of the following tools: (2 marks)**

- **i. Palettes:** A persistent window or area containing a set of tools, colors, or patterns (common in design software like Photoshop). It allows users to quickly switch between different modes or resources.
    
- **ii. Dialog Boxes:** Temporary windows that appear to request information from the user or provide a notification. They often interrupt the workflow until dismissed (modal) or allow parallel interaction (modeless).
    

**e. Briefly explain the following terms of interaction: (6 marks)**

- **(i) Intention:** The specific goal or desired outcome the user wants to achieve.
    
- **(ii) Task:** The sequence of operations or manipulations the user performs on the system to achieve their intention.
    
- **(iii) System:** The computer, application, or device the user is interacting with.
    
- **(iv) User:** The human operator interacting with the system.
    
- **(v) Core Language:** The language or set of attributes describing the system's state and computational capabilities (how the system "thinks").
    
- **(vi) Task Language:** The language or set of attributes describing the user's psychological state and perspective on the task (how the user "thinks").
    

## Question 2 (15 Marks)

a. What is Human-Computer Interaction? (2.5 marks)

Human-Computer Interaction (HCI) is a multidisciplinary field of study focusing on the design, evaluation, and implementation of interactive computing systems for human use and the study of major phenomena surrounding them.

**b. List five (5) disciplines involved in HCI. (2.5 marks)**

1. Computer Science
    
2. Cognitive Psychology
    
3. Ergonomics / Human Factors
    
4. Sociology
    
5. Graphic Design (or Engineering, Linguistics)
    

**c. Mention and explain the four (4) key components of HCI. (10 marks)**

1. **The User (Human):** The individual or group interacting with the system. This involves understanding human cognitive capabilities, memory, physical limitations, and sensory processing.
    
2. **The Task:** The goal-oriented activity the user wishes to perform. Designing for the task involves understanding the workflow, complexity, and structure of the work.
    
3. **The Tool (Interface/System):** The technology (hardware and software) provided to the user. This includes the input/output devices and the interaction style (GUI, CLI).
    
4. **The Context (Environment):** The physical and social setting in which the interaction takes place (e.g., a noisy factory, a quiet office, mobile usage while walking).
    

## Question 3 (15 Marks)

a. Explain the two most important characteristics of a good design that enhance ease of use. (2 marks)

(Note: There are several, but these are two primary ones)

1. **Visibility:** The more visible functions are, the more likely users will know what to do next. The system status should always be clearly observable.
    
2. **Feedback:** The system should provide immediate and clear information back to the user about what action has been done and what has been accomplished (e.g., a button changing color when clicked).
    

**b. Describe Long-Term Memory based on function, capacity and duration. (2.5 marks)**

- **Function:** Stores information, knowledge, and experiential data for long periods. It allows us to recall facts, procedures, and past events.
    
- **Capacity:** Theoretically unlimited (huge).
    
- **Duration:** Potentially permanent (information can last a lifetime, though access may degrade).
    

**c. Draw a well labelled diagram of the structure of human memory that shows the three parts of memory. (8 marks)**

_(Text representation of the diagram)_

```
[ Input ] ---> [ Sensory Memory ] ---> [ Short-Term / Working Memory ] <---> [ Long-Term Memory ]
                    ^                           ^              ^
                    |                           |              |
                (Attention)                (Rehearsal)     (Retrieval)
```

- **Sensory Memory:** Iconic (Visual), Echoic (Aural), Haptic (Touch).
    
- **STM:** Temporary holding, limited capacity (7 +/- 2 items).
    
- **LTM:** Permanent storage.
    

d. Briefly describe the interplay between the three parts of the human memory. (2.5 marks)

Information enters via Sensory Memory from the environment. If paid attention to, it moves to Short-Term Memory (STM). In STM, information is processed; if it is rehearsed, it moves to Long-Term Memory (LTM) for storage. To use knowledge, information is retrieved from LTM back into STM/Working Memory.

## Question 4 (15 Marks)

**a. What are the two types of human errors that usually originate from users? (1 mark)**

1. **Slips**
    
2. **Mistakes**
    

**i. Explain how each of the two human errors manifests. (3 marks)**

- **Slips:** Occur when the user has the **correct intention** but performs the **wrong action**. This usually happens in skilled/automatic behavior (e.g., typing "teh" instead of "the" due to poor finger coordination).
    
- **Mistakes:** Occur when the user has the **wrong intention** (and performs the action that matches that wrong intention). This happens due to incorrect understanding or a flaw in the mental model (e.g., clicking a "Format" button thinking it will just clear text, when it actually erases the disk).
    

**b. Compare the following interaction styles... (6 marks)**

|   |   |   |
|---|---|---|
|**Style**|**Advantage**|**Disadvantage**|
|**i. Command Line Interface (CLI)**|Powerful, flexible, and scriptable; expert users can work very fast.|Steep learning curve; requires memorization of commands (recall over recognition).|
|**ii. Graphical User Interface (GUI)**|Intuitive; relies on recognition rather than recall; easier for beginners.|Can be resource-intensive; navigating menus can be slower than typing a known command.|
|**iii. Natural Language**|No learning required (uses everyday speech); highly familiar.|Ambiguous; difficult for the system to parse complex or vague sentences accurately.|

**c. Give three examples of good practice for designing arrangement of controls and displays. (3 marks)**

1. **Functional Grouping:** Group related controls together (e.g., all font editing tools in one box).
    
2. **Sequential Order:** Arrange controls to reflect the natural flow of the task (e.g., Top-to-bottom or Left-to-right).
    
3. **Frequency of Use:** Place the most frequently used controls in the most accessible positions.
    

**d. Explain how Gulfs of Execution and the Gulfs of Evaluation are used to evaluate the effectiveness of an interaction. (2 marks)**

- **Gulf of Execution:** Evaluates how easy it is for the user to understand how to operate the device to achieve their goal. (Does the system allow what the user wants to do?)
    
- **Gulf of Evaluation:** Evaluates how easy it is for the user to perceive the state of the system and determine if their goal was achieved. (Can the user tell if it worked?)
    
- Small gulfs indicate effective interaction; large gulfs indicate poor design.
    

## Question 5 (15 Marks)

a. What is the focus of Norman's Model of Interaction? (0.5 marks)

The focus is on the cognitive processing of the user, specifically identifying where difficulties occur in bridging the gap between the user's goals and the physical system.

**b. What are the seven stages in Norman's model? (3.5 marks)**

1. Forming the **Goal**
    
2. Forming the **Intention** (Plan)
    
3. Specifying the **Action** sequence
    
4. **Executing** the Action
    
5. **Perceiving** the System State
    
6. **Interpreting** the State
    
7. **Evaluating** the Outcome (Comparing state with goal)
    

**c. Use the Execution-Evaluation cycle diagram to explain how the seven stages are implemented. (11 marks)**

- **The Goal:** The user starts with a goal (e.g., "I want to read in the dark").
    
- **The Gulf of Execution (Bridging the Goal to the World):**
    
    1. **Plan/Intention:** The user decides to switch on the light.
        
    2. **Specify:** The user determines they need to flip the specific switch on the wall.
        
    3. **Perform:** The user physically flips the switch.
        
- **The Physical System (World):** The light turns on (or doesn't).
    
- **The Gulf of Evaluation (Bridging the World back to the Goal):**
    
    1. **Perceive:** The user sees the light levels in the room change.
        
    2. **Interpret:** The user processes that "the room is now bright."
        
    3. **Compare:** The user matches this new state against the original goal ("I can read now"). If they match, the cycle is complete.
        

## Question 6 (15 Marks)

**a. With the aid of diagram, explain the interaction design process using its four main phases and iteration-prototyping loop. (12 marks)**

_(Description of Diagram Flow)_

1. **Identify Needs/Establish Requirements:** Understanding who the users are and what they are trying to achieve.
    
2. **Design Alternatives:** Generating conceptual models and different design ideas to meet those needs.
    
3. **Prototyping:** Building interactive versions of the designs (low-fidelity paper models or high-fidelity software) so they can be communicated and tested.
    
4. **Evaluation:** Testing the prototypes with users to see if requirements are met.
    
5. **Iteration Loop:** The results of _Evaluation_ feed back into _Design Alternatives_ or _Identify Needs_, creating a cycle that repeats until the product is satisfactory.
    

b. Which of the interaction design phases focused on user interest and how? (1 mark)

Identify Needs / Establish Requirements. This phase focuses entirely on the user's interest by gathering data regarding their goals, characteristics, tasks, and environment before any design work begins.

**c. What are the two main structures usually considered in Navigation Design? (2 marks)**

1. **Hierarchical Structure:** Information is organized in a tree-like structure (Parent -> Child). Good for deep content.
    
2. Network Structure: Information is linked freely (Web-like), allowing users to move from any node to various other nodes. Good for associative browsing.
    
    (Alternatively: Local Navigation and Global Navigation)