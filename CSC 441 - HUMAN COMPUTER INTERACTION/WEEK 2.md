# Week 2: Understanding the Human
## Core Principle

To design effective interfaces, we must understand how humans process information. We can model this as a system with **inputs** (how we receive information) and **outputs** (how we act). This is sometimes called the **Human Processor Model**.

## a. Input-Output Channels

### 1. Input Channels (The Senses)

How humans receive data from the computer.

#### **Vision (Dominant Channel)**

- **What it is:** The complex sense of light, color, depth, movement, and patterns.
    
- **Relevance to HCI:** This is the primary channel for most interfaces. It governs:
    
    - **Layout:** Where elements are placed on a screen.
        
    - **Typography:** The style and size of text. Clear, legible fonts are crucial.
        
    - **Iconography:** The design of icons (e.g., the 'save' floppy disk, the 'settings' gear).
        
- **Design Considerations:**
    
    - **Visual Acuity:** How clearly a user can see. Not everyone has 20/20 vision.
        
    - **Color Blindness:** A significant portion of the population (especially males) has difficulty distinguishing between colors, most commonly red and green.
        
    - **Reading Speed:** Users scan, they don't read every word.
        
- **Real-World Example:** A well-designed dashboard uses high-contrast colors (e.g., dark text on a light background) for acuity. It **avoids using only color** to convey information (e.g., a "red" dot for "error"). Instead, it pairs the color with an icon (like an 'X') or text, making it accessible to color-blind users.
    

#### **Hearing (Aural Channel)**

- **What it is:** Sensing sound, including pitch, timbre (tone quality), and location.
    
- **Relevance to HCI:**
    
    - Provides essential non-visual feedback.
        
    - Crucial for accessibility (e.g., screen readers for visually impaired users).
        
- **Real-World Example:** Differentiate between:
    
    - **Alerts:** A sharp, loud 'error' sound. This demands immediate attention and interrupts the user's workflow.
        
    - **Feedback:** The soft 'swoosh' of a sent email or the 'click' of a digital button. This _confirms_ an action was successful without being disruptive.
        

#### **Touch (Haptic Channel)**

- **What it is:** Sensing pressure, temperature, and texture.
    
- **Relevance to HCI:** Used for tactile feedback.
    
- **Real-World Example:** When you type on your smartphone's glass screen, the small **vibration "buzz"** you feel under your finger is haptic feedback. It confirms that the "key" was pressed, which makes typing on a flat, non-moving surface feel more responsive and accurate. This is also heavily used in game controllers (e.g., rumbling during an explosion).
    

### 2. Output Channels (Motor Control)

How humans generate actions and interact with the system.

#### **Movement (Motor System)**

- **What it is:** The coordination of muscles for actions like typing, clicking, dragging, and gesturing.
    
- **Relevance to HCI:** This influences the design of all input devices (keyboards, mice, touchscreens) and, critically, the placement of interactive elements.
    
- **Key Concept: Fitts's Law**
    
    - This is a fundamental law in HCI that **predicts the time it takes to move to and click a target.**
        
    - The time depends on two factors:
        
        1. **Distance** to the target.
            
        2. **Size** of the target.
            
    - **In short: Bigger targets that are closer are** _**much**_ **faster and easier to click.**
        
- **Real-World Example (Fitts's Law):**
    
    - **Good Design:** The "close" button on a pop-up window is large and placed in a corner. The edges of the screen act as an "infinitely large" target because you can't overshoot them with your mouse, making them very fast to hit.
        
    - **Bad Design:** A long list of tiny text links on a mobile phone. The targets are small and close together, leading to high error rates (tapping the wrong link).
        
- **Health Consideration:** Poor design can lead to **Repetitive Strain Injuries (RSI)**. Ergonomic keyboards and vertical mice are designed to align with the body's natural posture, reducing strain.
    

## b. Human Memory

Memory structure dictates how much information a user can process and retain.

### 1. Sensory Memory

- **What it is:** An ultra-short-term "buffer" for stimuli received through the senses.
    
    - **Iconic Memory:** For visual stimuli (lasts < 1 second).
        
    - **Echoic Memory:** For aural stimuli (lasts 2-4 seconds).
        
    - **Haptic Memory:** For touch stimuli.
        
- **Function:** It holds sensory information just long enough for the brain to decide if it's important enough to pass on to working memory. It's constantly being overwritten.
    
- **Real-World Example:** You see a flash of lightning (iconic memory). The visual 'afterimage' persists for a fraction of a second, allowing your brain to process "that was lightning." Or, if you're not paying attention and someone speaks, you can often "re-hear" the last few words they said (echoic memory) if you focus quickly.
    

### 2. Working Memory (Short-Term Memory)

- **What it is:** The "scratch-pad" or "CPU" of the mind. It's where active thinking, calculation, and processing happen.
    
- **Function:**
    
    - Holds a **limited amount of information**.
        
    - Holds it for a **short period** (around 15-30 seconds without active rehearsal).
        
- **Key Concept: Chunking**
    
    - Working memory's capacity is famously described as **"The Magical Number Seven, Plus or Minus Two"** (or 7 ± 2) chunks of information.
        
    - A **"chunk"** is a single, meaningful unit of information.
        
    - **Example:** The number sequence `19842001` is 8 chunks. But `1984` and `2001` are two (meaningful) chunks. "Chunking" is the process of grouping items to make them easier to remember. This is why phone numbers (`555-1234`) and credit card numbers are grouped.
        
- **HCI Application: Minimize Cognitive Load**
    
    - An interface should **never** force the user to rely on their working memory.
        
    - **Bad Design:** A website that shows a confirmation code on one page and then asks you to type it on the _next_ page (forcing you to remember it).
        
    - **Good Design:** Keeping essential information (like items in a shopping cart) visible at all times.
        
- **Key Concept: Recognition over Recall**
    
    - **Recall:** Forcing a user to remember (e.g., "What is the command-line syntax to copy a file?"). This is difficult and high-load.
        
    - **Recognition:** Allowing a user to _see_ options and choose (e.g., a "File" menu with a "Copy" option and a familiar icon). This is easy and low-load.
        
    - **Principle:** Modern graphical interfaces (GUIs) are built almost entirely on the principle of recognition, not recall.
        

### 3. Long-Term Memory (LTM)

- **What it is:** The "hard drive" of the brain. The permanent, limitless (theoretically) store of all our knowledge.
    
- **Function:**
    
    - **Capacity:** Huge.
        
    - **Access Time:** Relatively slow (compared to working memory).
        
    - **Decay:** Very slow, if at all. Information is stored here from working memory through **rehearsal** (practice, repetition).
        
- **Structure of LTM:**
    
    - **Episodic Memory:** Memory of _events_ and _experiences_ in a serial form (e.g., "I remember eating breakfast this morning and spilling my coffee.").
        
    - **Semantic Memory:** A structured record of _facts_, _concepts_, and _skills_ (e.g., "I know that coffee is a hot beverage and that breakfast is the first meal of the day.").
        
- **HCI Application: Consistency and Mental Models**
    
    - Interfaces should leverage a user's LTM.
        
    - **Key Concept: Mental Model:** A user's internal belief about how a system works. This is built from their past experiences (LTM).
        
    - **Real-World Example:** Everyone has a mental model for a "shopping cart." If an e-commerce site uses a "shopping bag" icon, it's fine. If adding an item to the cart _deleted_ a previous item, it would violate the user's mental model and cause massive confusion.
        
    - **Consistency:** This is why `Ctrl+Z` (or `Cmd+Z`) is _always_ "Undo" and a trash can icon _always_ means "Delete." By using these established conventions, a new application feels instantly familiar, as the user can apply their existing knowledge (LTM).



## c. Thinking (Reasoning and Problem Solving)

Users are actively thinking while interacting with a system, trying to make sense of it and achieve their goals.

### 1. Reasoning

- **What it is:** The process of drawing conclusions from evidence. Users constantly try to infer the system's state or the cause of an error.
    
    - **Inductive Reasoning:** Generalizing from specific observations. (e.g., "Every time I click this button, the app crashes. Therefore, this button is broken.")
        
    - **Deductive Reasoning:** Using general rules to understand a specific case. (e.g., "The manual says `Ctrl+S` saves the document. Therefore, if I press `Ctrl+S`, my file will be saved.")
        
- **Design Implication:** Don't make the user guess. The system should be transparent.
    
    - **Key Principle: Visibility of System Status.** A user shouldn't have to _reason_ about what the system is doing. It should be obvious.
        
    - **Real-World Example:** When you upload a file, a good design shows a progress bar and a percentage ("Uploading... 75%"). A bad design shows nothing, forcing the user to reason: "Is it working? Did it crash? Did I even click the button?"
        

### 2. Problem Solving

- **What it is:** The process of moving from an initial state (the problem) to a desired goal state (the solution).
    
- **Key Concept: Means-Ends Analysis**
    
    - This is a common problem-solving strategy where a user breaks down a large goal into smaller, manageable sub-goals.
        
    - **Example:** Goal: "Book a trip." Sub-goals: 1. Find flights. 2. Find a hotel. 3. Rent a car. 4. Pay for it all.
        
- **Design Implication:** Support the user's sub-goals.
    
    - **Real-World Example:** A multi-step "wizard" for setting up new software. It breaks the complex task ("Install this program") into simple, sequential steps ("Step 1: Accept License," "Step 2: Choose Install Location," "Step 3: Finish"). This guides the user through the process and makes the problem feel solvable.
        

## d. Human Emotions

Emotion is a critical, and often overlooked, part of the User Experience (UX).

- **Impact on Interaction:**
    
    - **Frustration:** Caused by errors, slow response times (`lag`), or confusing design. Frustration leads to errors and system abandonment.
        
    - **Joy/Satisfaction:** Caused by success, beautiful aesthetics, or "delightful" micro-interactions (e.g., the little animation when you "like" a post). This builds loyalty.
        
- **Key Concept: Aesthetic-Usability Effect**
    
    - **What it is:** A cognitive bias where users perceive aesthetically pleasing designs as _more usable_ and more trustworthy, regardless of their actual functionality.
        
    - **Implication:** Good visual design is not just "decoration"; it is a core part of building a positive user experience.
        
- **Design Implication:** Design for positive emotions.
    
    - **Aesthetics:** Invest in a clean, professional, and pleasing visual design.
        
    - **Error Handling:** Prevent errors first. When they must happen, provide constructive, polite, and human-readable feedback. (e.g., "Page Not Found" vs. "Error 404").
        

## e. Individual Differences

Users are not all the same. A "one-size-fits-all" approach will fail a large portion of your audience.

- **Key Differences to Consider:**
    
    - **Physical:** Hand size (e.g., for mobile design), visual acuity (vision impairment), motor skills (tremors, arthritis).
        
    - **Cognitive:** Technical expertise (beginner vs. expert), learning speed, cultural mental models (e.g., colors can have different meanings in different cultures).
        
    - **Personality:** Willingness to explore vs. need for structure.
        
- **Design Goal: Universal Usability**
    
    - The goal is to design interfaces that are accessible and usable by the largest possible range of users.
        
- **Accommodation Strategies:**
    
    - **Customization:** Offer options (e.g., adjustable font sizes, "Dark Mode," remappable keys in a game).
        
    - **Accessibility Standards:** Adhere to established guidelines like the **Web Content Accessibility Guidelines (WCAG)**, which provide a framework for making web content accessible to people with disabilities.
        

## f. Psychology of Design (Recap)

This concept unifies everything. It is the practical application of understanding the human mind (psychology) to the creation of systems (design).

- **Core Goal:** To create systems where the user's **Mental Model** (what the user _believes_ about how it works) matches the system's actual **Operational Model** (how it _actually_ works).
    
- **How we do this:** By using core HCI principles:
    
    - **Affordances:** A property of an object that suggests how it can be used. (A button _affords_ pushing).
        
    - **Visibility:** Making the system's state and possible actions obvious.
        
    - **Feedback:** Communicating the result of an action.
        
    - **Constraints:** Limiting the user's possible actions to prevent errors. (e.g., "graying out" a "Save" button when there are no changes to save).
        

## Illustrative Scenarios

### 1. Video Game Sensory Channels (Input-Output)

- **Example:** A First-Person Shooter (FPS) Game.
    
- **Sight (Input):** User focuses on the crosshair, environment, and HUD (Heads-Up Display).
    
    - **Feedback:** Health bar turns red and decreases.
        
    - **Guidance:** A waypoint marker on the screen shows the objective.
        
- **Sound (Input):** User listens for environmental awareness.
    
    - **Feedback:** A sharp "thud" or "whine" sound when taking damage.
        
    - **Guidance:** Positional audio of enemy footsteps or gunfire helps the player locate unseen threats.
        
- **Touch/Haptic (Output/Feedback Loop):** User's motor system presses buttons.
    
    - **Feedback:** The controller **vibrates** (haptics) when an explosion happens nearby, providing a physical confirmation of the event.
        
    - **Guidance:** The trigger button's spring-loaded shape _affords_ pulling it.
        

### 2. Reducing Cognitive Load on an Online Form (Working Memory)

- **Scenario:** A multi-page job application asks for your employer's address on Page 3, which is the same as the mailing address you entered on Page 1.
    
- **Problem:** The bad design forces you to **Recall** this information, placing a high load on your working memory.
    
- **Solution 1 (Recognition over Recall):**
    
    - On Page 3, add a checkbox: `[ ] Same as Mailing Address`.
        
    - Checking this box auto-fills the fields. The user simply has to _recognize_ the option, not _recall_ the data.
        
- **Solution 2 (High Visibility):**
    
    - On Page 3, display the mailing address (from Page 1) in a small, non-editable summary box on the side. This keeps the information visible, removing the memory burden.
        

### 3. Preventing Emotional Frustration (Emotions & Error Handling)

- **Scenario:** You spend an hour editing a document in a web app. You click "Save," and a message pops up: "Session timed out." All your work is lost.
    
- **Analysis:** This is a catastrophic error that triggers extreme frustration because the system failed to provide feedback and constraints.
    
- **Redesign to Prevent Frustration:**
    
    - **Proactive Feedback:** 5 minutes before timeout, show a non-intrusive banner: "Your session will expire in 5 minutes. [Click here to extend]."
        
    - **Robust Error Handling:** If the session _does_ expire and the user clicks "Save," _do not_ lose the work. Instead, save the changes locally in the browser (`localStorage`) and show a message: "Your session expired. We've saved your work in this browser. Please log in again to sync your changes." This turns a catastrophe into a minor, recoverable inconvenience.
        

### 4. Designing for Individual Differences (Universal Usability)

- **Goal:** Design a new smartphone app for both young adults and senior citizens.
    
- **Accommodation Strategies:**
    
    - **Visual Acuity:** Offer variable text sizes and a high-contrast color scheme (WCAG).
        
    - **Motor Control/Tremor:** Use large, "fat-finger friendly" touch targets with ample spacing (Fitts's Law).
        
    - **Cognitive/Mental Model:** Provide a simple, linear navigation (for seniors) and a faster, nested menu (for experts). Use standard icons (LTM).
        
    - **Cognitive/Processing Speed:** Chunk information into small, digestible screens.
        
    - **Personality:** Provide clear "Help" overlays (for structure-seekers) but allow experts to dismiss them.