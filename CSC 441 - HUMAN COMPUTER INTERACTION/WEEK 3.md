# Week 3: Understanding the Interaction

**Module Goal:** This week, we move from just building _functional_ programs to engineering _usable_ systems. The focus is on the theories and models that explain how humans and computers communicate.

### a. Models of Interaction

#### 1. Norman’s Model of Interaction (NMI)

This is a foundational model in HCI, developed by Don Norman. It describes interaction as a cycle with two main phases: **Execution** (doing things) and **Evaluation** (checking how it went).

The cycle breaks down into seven user-centered stages.

> **The Seven Stages of Action:**
> 
> 1. **Establishing the Goal:** (What do I want to do?)
>     
> 2. **Forming the Intention:** (What specific command or action will achieve my goal?)
>     
> 3. **Specifying the Action Sequence:** (How do I execute that command? Move the mouse? Press keys?)
>     
> 4. **Executing the Action:** (The physical act of moving the mouse, clicking, or typing.)
>     
> 5. **Perceiving the System State:** (What did the system do? What's on the screen?)
>     
> 6. **Interpreting the System State:** (What does that new screen, sound, or message _mean_?)
>     
> 7. **Evaluating the System State:** (Did what happened match my goal? Am I done? Or do I need to try again?)
>     

**Real-World Example: Using a Photo Editing App**

Let's apply the 7 stages to a simple task:

- **1. Goal:** "This photo from my vacation is too dark."
    
- **2. Intention:** "I'll use the 'Brightness' tool to fix it."
    
- **3. Action Sequence:** "I need to find the 'Adjustments' menu, then select 'Brightness', and then move the slider to the right."
    
- **4. Execution:** _User physically moves the mouse, clicks on 'Adjustments', clicks 'Brightness', and drags the slider._
    
- **5. Perception:** "The photo on the screen is getting brighter as I drag the slider."
    
- **6. Interpretation:** "The slider is successfully controlling the image's brightness."
    
- **7. Evaluation:** "Okay, that looks much better. My goal is complete."
    

If the user evaluated the state and thought, "Now it's too bright," they would form a new goal ("Make it a little darker") and restart the cycle.

#### 2. The Gulfs of Execution and Evaluation

Norman's model is most famous for identifying two "gulfs," or gaps, that designers must bridge to create a usable system.

**The Gulf of Execution**

- **The Question:** "How do I do the thing I want to do?"
    
- **Definition:** The gap between the user's _intention_ and the _actions_ the system allows.
    
- **A Wide Gulf (Bad Design):** A website with a tiny, un-labeled, non-standard icon for "Save." The user wants to save, but has no idea how. They have to hunt for the action.
    
- **Bridging the Gulf (Good Design):** A large, clear button labeled "Save." This provides **discoverability** and **affordance** (it _looks_ clickable), making the user's intended action obvious and easy to execute.
    

**The Gulf of Evaluation**

- **The Question:** "Did I do it? What happened?"
    
- **Definition:** The gap between the system's _actual state_ and the user's _ability to understand it_.
    
- **A Wide Gulf (Bad Design):** You click "Submit" on a web form, and the page just reloads, showing the same blank form. You have no idea if your information was sent or if there was an error.
    
- **Bridging the Gulf (Good Design):** You click "Submit," and a clear message appears: "Success! Your form has been submitted." Or, if it failed, "Error: The email address is invalid." This is called **feedback**, and it's crucial for bridging this gulf.
    

#### 3. Human Error: Slips vs. Mistakes

Understanding the gulfs helps us categorize errors.

- **Slips (An Execution Error):**
    
    - **What it is:** You had the right goal and the right plan, but you messed up the _execution_.
        
    - **Common Cause:** Poor interface design that makes the wrong action too easy to perform.
        
    - **Real-World Example:** Intending to click "Save" but accidentally clicking the "Delete" button because they are right next to each other. Or, a simple typo: you _meant_ to type "hello" but your fingers "slipped" and you typed "jello."
        
    - **How to fix:** Better design (e.g., add spacing between buttons, add a confirmation step for "Delete").
        
- **Mistakes (An Evaluation/Goal Error):**
    
    - **What it is:** You successfully executed your plan... but the plan itself was wrong. This is due to a misunderstanding of the system.
        
    - **Common Cause:** The user's "mental model" (their understanding of how the system works) is incorrect.
        
    - **Real-World Example:** A user wants to remove an email from a recipient's inbox. They go to their _own_ "Sent" folder and delete the email, thinking this will "un-send" it. Their action was executed perfectly, but their goal was based on a flawed understanding.
        
    - **How to fix:** This is harder. It requires better training, clearer labels, or redesigning the system to match user expectations.
        

#### 4. The Interaction Framework

This framework models the _system's_ side of the interaction, which Norman's model mostly ignores. It has four components:

1. **User (U):** The person with a goal.
    
2. **System (S):** The computer, hardware, and software.
    
3. **Input (I):** Devices for the user to "talk" to the system (e.g., keyboard, mouse, touchscreen).
    
4. **Output (O):** Devices for the system to "talk" back to the user (e.g., screen, speakers, haptics).
    

The interaction happens in a loop of four translations:

- **Articulation (User → Input):** The user translates their psychological goal into a physical action (e.g., thinking "send this message" and then physically pressing the "Send" button).
    
- **Performance (Input → System):** The system translates the input action into internal commands (e.g., the button click is processed by the OS and the app's code).
    
- **Presentation (System → Output):** The system translates its new state into an understandable output (e.g., the app's internal code now renders the text "Message Sent" on the screen).
    
- **Observation (Output → User):** The user perceives and interprets the output (e.g., the user sees "Message Sent" and understands their goal is complete).
    

### b. Ergonomics & Interaction Styles

#### 1. Ergonomics (Human Factors)

Ergonomics is about designing the _physical_ interaction to be safe, comfortable, and efficient. It considers the human body and its environment.

**Key Concerns of Ergonomics:**

- **Physical Hardware:**
    
    - **Controls:** Are buttons logically grouped? (e.g., a car's climate controls are all in one place). Are they easy to find and use, especially under pressure?
        
    - **Physical Layout:** Is the monitor at the right height? Is the chair supportive? This is crucial for preventing **Health Issues** like **Repetitive Strain Injury (RSI)** or Carpal Tunnel Syndrome from poor keyboard and mouse use.
        
- **Environment:**
    
    - **Factors:** Lighting, temperature, noise levels.
        
    - **Real-World Example:** An interface for a factory floor must be legible under bright fluorescent lights and loud (so it might use bright, flashing lights for alerts, not quiet beeps). An office interface has different requirements.
        
- **Use of Color:**
    
    - Colors should be distinct and follow conventions (e.g., Red for "Stop" or "Error," Green for "Go" or "Success").
        
    - Must consider color blindness and ensure text is still legible (high contrast).
        

#### 2. Interaction Styles

This is the "dialog" between the user and the computer. Different styles have different trade-offs.

|   |   |   |
|---|---|---|
|**Style**|**Description**|**Good For... (Examples)**|
|**Command Line (CLI)**|User types commands at a prompt.|**Experts & technical tasks.** (e.g., `git`, `ssh`). It's fast and powerful if you memorize the commands, but impossible for novices.|
|**Menus**|User selects from a list of options.|**Novices & exploring options.** (e.g., File/Edit menus). Relies on **recognition** (seeing the option) not **recall** (remembering the command).|
|**Natural Language**|User speaks or types in "normal" language.|**Casual users & complex queries.** (e.g., "Hey Siri, what's the weather?" or searching on Google). Very difficult for the system to interpret correctly.|
|**Form-Fills / Spreadsheets**|User enters data into clearly defined fields.|**Data entry.** (e.g., Online shopping checkouts, registration forms, Excel). Very structured and efficient for this one task.|
|**WIMP**|(See below)|**General purpose computing.** This is the dominant style for desktops and laptops.|

### c. The WIMP Interface

WIMP is the dominant style of Graphical User Interface (GUI). It stands for:

- **Windows:** Separate, scrollable areas of the screen. They allow users to see multiple applications or documents at once, providing context.
    
- **Icons:** Small, visual representations of objects (files, folders, apps) or actions (cut, paste, print).
    
- **Menus:** Lists of commands that appear when requested (pull-down, pop-up).
    
- **Pointer:** A screen cursor controlled by a mouse, trackpad, or other pointing device.
    

The WIMP style is the classic example of **Direct Manipulation**: users interact directly with visual objects on the screen (e.g., _dragging_ a file icon into a trash can icon) and get immediate, visible feedback.

### d. Interactivity

Interactivity refers to the speed and quality of the dialogue between the user and the system.

- **High Interactivity:**
    
    - **What it is:** Rapid feedback and continuous control.
        
    - **Example:** Playing a video game. You press "jump," and the character jumps _instantly_. Or, dragging a slider in a photo app and seeing the image change in real-time.
        
    - **Benefit:** Essential for error prevention. If you make a slip, you see the bad result immediately and can correct it.
        
- **Low Interactivity:**
    
    - **What it is:** Long delays between input and output.
        
    - **Example:** Batch processing. You submit a job (e.g., "run payroll for 10,000 employees") and come back hours later to get the results. There is no back-and-forth.
        

### e. Context of Interaction & User Experience (UX)

#### 1. Context of Interaction

You cannot design a system in a vacuum. The _context_ of where and how it will be used is critically important.

- **Physical Context:** Where is the user?
    
    - **Example:** A mobile banking app must be usable with one hand while the user is standing on a crowded train. A hospital kiosk app must have large text for users with poor vision and be cleanable.
        
- **Social Context:** Who is the user with?
    
    - **Example:** A system playing a loud sound might be fine at home but embarrassing in a quiet office.
        
- **Organizational Context:** What are the rules of the environment?
    
    - **Example:** A system for managing patient records in a hospital isn't just for one doctor. It must be usable by nurses, pharmacists, and billing, all while following strict legal privacy rules (like HIPAA). The design is heavily constrained by these rules.
        

#### 2. User Experience (UX), Engagement, and Fun

Early HCI focused only on efficiency and effectiveness (usability). Modern HCI also cares about the broader **User Experience (UX)**.

- **Usability vs. UX:**
    
    - **Usability:** Can the user achieve their goal? (e.g., "Can I transfer money in this banking app?")
        
    - **User Experience (UX):** How did the user _feel_ while doing it? Were they satisfied? Stressed? Delighted?
        
- **Why UX Matters:** For non-work tools (games, shopping, social media), "fun" and "engagement" are the _primary_ goals. Even for work tools, a positive, aesthetically pleasing design can make users feel more loyal and even perceive the system as _more usable_.
    
- **Real-World Example:** Two airlines have apps that both let you book a flight (both are _usable_). App A is ugly, slow, and confusing. App B is beautiful, fast, and has smooth animations. You will _prefer_ using App B and feel better about that airline. That's the power of good UX.
    

### f. Illustrative Scenarios: Applying HCI Concepts

Here are practical examples showing how these concepts work in the real world.

#### 1. Scenario: Voice Speaker vs. Graphical App

This shows how different interaction styles handle the Gulfs of Execution and Evaluation.

|   |   |   |
|---|---|---|
|**HCI Concept**|**Voice Interface (Smart Speaker)**|**GUI (Desktop App)**|
|**Gulf of Execution**|**Bridged by Natural Language.** The user just states their goal ("Hey Google, play jazz").<br><br>  <br><br>  <br><br>**Challenge:** The _system's_ gulf is wide. It must use complex AI (NLP) to understand the _infinite_ ways a user can phrase a command.|**Bridged by Visibility & Affordance.** The user clicks visible icons and menus.<br><br>  <br><br>  <br><br>**Challenge:** The _user's_ gulf can be wide if they don't know _which_ icon to click. The system constrains actions to what is visible.|
|**Gulf of Evaluation**|**Bridged by Auditory Feedback.** The user listens for a spoken reply ("Playing jazz on Spotify").<br><br>  <br><br>  <br><br>**Challenge:** This feedback is **transient** (it disappears). If you mishear it or forget it, it's gone.|**Bridged by Visual Feedback.** The user sees changes on the screen (a progress bar, a new window).<br><br>  <br><br>  <br><br>**Challenge:** This feedback is **persistent**. It's easy to check, but can be overwhelming (too many notifications).|

**Conclusion:** For a simple, known task ("play music"), the voice interface has a _smaller_ Gulf of Execution for the user. But its _transient_ feedback can make the Gulf of Evaluation _wider_ if the user is distracted.

#### 2. Scenario: Ergonomics for a Kiosk vs. Office PC

This shows how the **Context of Interaction** changes everything about design.

|                      |                                                                                                                                                |                                                                                                                             |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Ergonomic Factor** | **Public Kiosk (Train Station)**                                                                                                               | **Standard Office Desktop**                                                                                                 |
| **Users**            | **Diverse & Hurried.** All ages, abilities, sizes. Standing, carrying luggage, distracted.                                                     | **Single & Stationary.** A trained employee, sitting for a long time in a controlled environment.                           |
| **Input Devices**    | **Durable & Simple.** Vandal-proof touchscreens, large metal keypads. Must be usable by people with disabilities (e.g., at wheelchair height). | **Comfortable & Adjustable.** Standard keyboard and mouse. Focus is on minimizing long-term RSI risk with wrist rests, etc. |
| **Display**          | **High-Brightness & Anti-Glare.** Must be visible in bright sunlight. Positioned for a _standing_ user to see without neck strain.             | **Standard Brightness & Matte.** Focus is on low-blue-light and readability for 8+ hours of use.                            |
| **Feedback**         | **Loud & Clear.** Must use loud beeps or visual flashes to be noticed over the noise of a train station.                                       | **Subtle & Quiet.** Can rely on small sounds or on-screen notifications that won't disturb coworkers.                       |

#### 3. Scenario: Interaction Styles in a Social Media App

Modern apps blend multiple styles to make a fluid experience.

|   |   |   |
|---|---|---|
|**Interaction Style**|**Example in App (e.g., Instagram)**|**Rationale (Why this style?)**|
|**Point-and-Click (WIMP)**|Tapping the "Like" (heart) icon or "Share" button.|**Speed & Low Effort.** Uses the WIMP principle of **affordance** (it _looks_ tappable). It's a simple, direct action.|
|**Direct Manipulation**|Swiping left/right to view stories, or "pull-to-refresh" the feed.|**Engagement & Control.** The action (finger movement) maps _directly_ to the result (page movement). This immediate, high-interactivity feedback feels fluid.|
|**Menus**|The persistent icon bar at the bottom (Home, Search, Profile).|**Navigation & Recognition.** This is a permanent menu. It keeps the most common actions _always visible_, reducing memory load. You recognize the icon; you don't have to recall where it is.|
|**Form-Fill**|Typing a caption for a post, or filling out your profile bio.|**Structured Data Entry.** Used when the system needs specific, constrained text input from the user (e.g., a 150-character limit on the bio).|