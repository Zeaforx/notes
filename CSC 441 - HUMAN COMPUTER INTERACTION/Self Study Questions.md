# CSC441: Human-Computer Interaction - Self-Study Solutions

This document provides detailed answers to the self-study questions outlined in the CSC441 course content for the 2025/2026 Academic Session.

## Week 1: Introduction to HCI

**1. Think about an app you use frequently. Identify one feature that you find particularly easy to use and one that is frustrating. Apply the principles of HCI (e.g., visibility, feedback, constraints, mappings) to explain why one is well-designed and the other is not.**

- **Good Design (e.g., WhatsApp Voice Message):**
    
    - **Feature:** Holding the microphone icon to record and sliding up to lock it for hands-free recording.
        
    - **Why:** It utilizes **Feedback** (the icon glows/changes, a timer starts) and **Affordance** (the slide-up animation visibly suggests the locking mechanism). It also uses **Constraints** (you cannot type while holding the mic, preventing errors).
        
- **Bad Design (e.g., A Banking App Login):**
    
    - **Feature:** Password field that does not tell you if you are using the wrong case (Caps Lock) or has strict, invisible rules for special characters.
        
    - **Why:** It lacks **Visibility** of system status (doesn't warn about Caps Lock) and fails to provide helpful **Feedback** (generic "Login Failed" message instead of "Invalid Character"). It violates the principle of **Mapping** if the error message appears far away from the input field.
        

**2.** The text describes a common error with word processors where "save" and "delete" are adjacent in a menu. How would you redesign **this menu to prevent this kind of user error? Sketch or describe your new menu layout.**

- **Description** of **Redesign:**
    
    - **Spatial Separation:** Move "Delete" to a different section of the menu entirely, perhaps under an "Edit" or "Manage" submenu, while keeping "Save" in the primary "File" menu.
        
    - **Color Coding:** Use a neutral or positive color (blue/green) for "Save" and a warning color (red) for "Delete."
        
    - **Constraint/Confirmation:** If "Delete" is clicked, introduce a **forcing function** (a confirmation dialog box: "Are you sure you want to delete?") to arrest the error before it executes.
        

**3.** Choose a simple physical object, like a stapler or a light switch. Analyze its design based **on the psychology of everyday things. What are its affordances and what kind of feedback does it provide?**

- **Object:** A Stapler.
    
- **Affordances:** The smooth, contoured top surface affords "pressing" with the palm. The gap between the arms affords "inserting" paper.
    
- **Feedback:**
    
    - **Tactile:** You feel the spring compress and the staple snap through the paper.
        
    - **Auditory:** The distinct "click-crunch" sound confirms the action is complete.
        
    - **Visual:** You can see the staple bent on the paper.
        
- **Why it is difficult for designers:** Designers suffer from the "Curse of Knowledge." They know how the internal mechanism works, so the external operation seems obvious to them.
    
- **Core Fallacy:** The assumption that "If I can use it, everyone can use it." Designers are not representative users.
    

## Week 2: Understanding the Human

**1.** Consider a video game you have played. What sensory channels (sight, sound, etc.) does it primarily engage? How does the game use these channels to provide feedback **and guide your actions?**

- **Sensory Channels:** Primarily **Visual** (Sight), **Auditory** (Sound), and **Haptic** (Touch/Vibration).
    
- **Feedback Application:**
    
    - **Visual:** Red flashing screen edges indicate low health (guiding you to retreat).
        
    - **Auditory:** Footsteps getting louder indicate an enemy approaching (guiding you to look around).
        
    - **Haptic:** The controller vibrates when you take damage or fire a weapon (confirming the action).
        

**2.** Think about an online **form you recently filled out. Did the form require you to remember information from a previous page? How could the design have been improved to reduce the cognitive load on your working memory?**

- **Problem:** Multi-step checkout forms often ask for a shipping address on page 1 and then ask you to confirm billing details on page 3 without showing the shipping address again.
    
- **Improvement:** Reduce cognitive load by:
    
    - **Recognition over Recall:** Display the previously entered information in a summary sidebar or at the top of the current page.
        
    - **Defaults:** Provide a checkbox for "Same as Shipping Address" so the user doesn't have to re-enter or remember if they typed it correctly.
        

**3.** Reflect on a time when you became frustrated with a software application. What specific interaction led to this **emotion, and how could the interface have been designed to prevent it?**

- **Scenario:** Waiting for a webpage to load with no indication of activity.
    
- **Emotion:** Anxiety and Frustration (uncertainty if the app has crashed).
    
- **Prevention:** Provide immediate **feedback**. A progress bar or a "spinner" animation informs the user the system is working (Output channel), which manages expectation and reduces negative emotional response.
    

**4.** A company wants to design a new smartphone application for both young adults and senior citizens. What are some of the potential individual differences you would need to **consider in the design, and how might you accommodate them?**

- **Sensory (Vision):** Seniors may have presbyopia.
    
    - _Accommodation:_ Allow dynamic text resizing and use high-contrast colors.
        
- **Motor Control:** Seniors may have reduced dexterity.
    
    - _Accommodation:_ Make touch targets (buttons) larger than standard (e.g., >48px) and increase spacing between active elements.
        
- **Cognitive:** Young adults may prefer shortcuts; seniors may prefer explicit instructions.
    
    - _Accommodation:_ Use clear labels instead of abstract icons (e.g., text saying "Settings" rather than just a gear icon).
        

## Week 3: Understanding the Interaction

**1.** Consider a voice-activated smart speaker. How does this interaction style **differ from a graphical user interface in terms of bridging the gulf of execution and evaluation?**

- **Gulf** of **Execution:** In Voice UI, this is harder because the "permissible actions" are invisible. You don't know the exact command syntax (e.g., "Play music" vs. "Start Spotify"). In a GUI, menus show you what is possible.
    
- **Gulf of Evaluation:** In Voice UI, the system state is often invisible. You don't know if it heard you until it replies. A GUI provides instant visual updates (hover states, pressed buttons). Voice UI requires audio confirmation to bridge this gulf.
    

**2.** What are the ergonomic considerations for a public kiosk at **a train station compared to a standard desktop computer in an office?**

- **Physical Environment:** The kiosk must accommodate standing users of varying heights (screen tilt), whereas office desks are adjustable for sitting.
    
- **Lighting/Glare:** Kiosks need anti-glare screens due to uncontrolled ambient lighting; offices have controlled lighting.
    
- **Robustness:** Kiosks require vandal-proof hardware (metal keyboards, toughened glass).
    
- **Privacy:** Kiosks need privacy filters on screens so bystanders can't see ticket details.
    

**3.** Think about the interaction you have with **your favorite social media app. What interaction styles does it use? How do these styles make the experience engaging?**

- **Styles:** **Direct Manipulation** (scrolling, pinching to zoom photos) and **WIMP/Menus** (settings, tabs).
    
- **Engagement:** Direct manipulation makes the interaction feel natural and physical. Infinite scrolling creates a flow state that keeps the user engaged without breaking the experience to click "Next Page."
    

**4. Compare the user experience of a car's built-in GPS (ubiquitous) versus a personal smartphone-based GPS (wearable/carried).**

- **Car GPS (Ubiquitous):**
    
    - _Pros:_ Larger screen, integrated with car audio (mutes music for directions), never runs out of battery.
        
    - _Cons:_ Input is difficult while driving (safety lockouts), map data often outdated.
        
- **Smartphone GPS (Carried):**
    
    - _Pros:_ Personalized settings, real-time traffic data, familiar interface.
        
    - _Cons:_ Small screen, drains battery, mounting it can be physically awkward (ergonomics).
        

## Week 4: HCI Design Principles (1)

**1.** Choose a complex task, such as booking a flight online. Write a detailed scenario describing **a person's goal and their expected interaction with a website to complete this task.**

- **Scenario:** "John, a businessman, needs to book a flight from Lagos to Abuja for a meeting next Tuesday morning. He wants the cheapest flight before 10 AM."
    
- **Steps:**
    
    1. John lands on homepage. Expects distinct "From" and "To" boxes.
        
    2. Selects dates using a visual calendar.
        
    3. Clicks "Search." Expects a loading indicator.
        
    4. Results appear. John expects to filter by "Price" and "Departure Time."
        
    5. Selects flight. Expects a clear summary of costs before entering card details.
        
    6. Confirmation email received immediately.
        

**2.** Imagine you are designing a new social networking site. What user research methods would you employ to ensure the design is truly user-focused? Justify your **choices.**

- **Interviews:** To understand deep motivations—why do people leave current platforms?
    
- **Personas:** Create archetypes (e.g., "The Influencer," "The Observer") to guide design decisions.
    
- **Surveys:** To gather quantitative data on feature preferences (e.g., "Do you prefer dark mode?").
    

**3.** Take a poorly designed website you've encountered. Sketch a new navigation structure for it and explain **how your design improves the user's ability to find information.**

- **Problem:** Deeply nested menus where "Contact Us" is hidden under "About" -> "Company" -> "Legal."
    
- **Redesign:**
    
    - **Global Navigation Bar:** Keep top-level categories persistent (Home, Products, Services, Contact).
        
    - **Breadcrumbs:** Add "Home > Services > Repairs" trails so users know where they are.
        
    - **Fat Footer:** Place essential links (Contact, FAQ) at the bottom of every page.
        
- **Benefit:** Reduces the number of clicks (interaction cost) to reach the goal.
    

**4.** Describe two different prototyping techniques you could use to test **the app's design before any code is written.**

- **Paper Prototyping:** Sketching screens on paper.
    
    - _Use:_ Quick, cheap testing of layout and flow. Good for early feedback.
        
- **Storyboarding:** A comic-strip style sequence showing the user context (when and where they use the app).
    
    - _Use:_ validates the concept and the user journey, not just the interface.
        

## Week 5: HCI Design Principles (2)

**1.** Using a pen and paper, create a wireframe for a **mobile application designed to order coffee. Your wireframe should include a homepage and a menu page.**

- **Description** for **Mental Wireframe:**
    
    - **Home Page:** Top Header (Logo + Cart Icon). Center: "Reorder Favorites" (Speed). Bottom: Large buttons for categories (Hot Coffee, Iced, Pastries). Bottom Nav: Home, Menu, Account.
        
    - **Menu Page:** List of items with thumbnails. Next to each item, a distinct "+" button. Top filter bar (Espresso, Latte, Tea).
        

**2. Explain why a low-fidelity wireframe is often more useful in the early stages of design than a high-fidelity visual mockup.**

- **Focus on Structure:** Low-fi prevents stakeholders from getting distracted by colors, fonts, or images. It forces conversation about flow, layout, and usability.
    
- **Cost of Change:** It is cheap and fast to discard a sketch. It is expensive and emotionally difficult to discard a pixel-perfect Photoshop mockup.
    

**3.** Consider an online game like tic-tac-toe. How would you divide the game's logic into the Model, View, and Controller components?

- **Model:** The data. The 3x3 grid array (e.g., `[X, O, null...]`) and the logic to check for a win condition.
    
- **View:** The visual representation. The HTML/CSS drawing the grid and the images of X and O.
    
- **Controller:** The input handler. It listens for the mouse click on a square, tells the Model to update the array, and tells the View to re-render.
    

**4.** What are the advantages of using a framework like MVC when building interactive systems, as opposed to putting all the **code in a single file?**

- **Modularity:** You can change the visual design (View) without breaking the game logic (Model).
    
- **Maintenance:** Easier to debug. If the score is wrong, look at the Model. If the color is wrong, look at the View.
    
- **Collaboration:** Designers can work on the View while programmers work on the Controller.
    

## Week 6: HCI Design Rules, Guidelines & Evaluation Techniques (1)

**1.** Find a web page or application that you believe violates one of the usability principles. Identify the principle and **explain what a better design would look like.**

- **Violation:** A website where clickable buttons look like plain text, and non-clickable headers look like 3D buttons.
    
- **Principle Violated:** **Visibility** and **Affordance**.
    
- **Better Design:** Use standard conventions—underline links or make buttons look raised/colored. Ensure elements that _look_ clickable _are_ clickable.
    

**2.** Explain in your own words how a UIMS **(User Interface Management System) can make the design process more efficient.**

- A UIMS (like using React or a UI Kit) provides pre-built components (buttons, sliders, windows) that handle their own drawing and input.
    
- **Efficiency:** The developer doesn't have to code "how to draw a button" every time. They just call the component. It ensures **Consistency** across the application automatically.
    

**3.** You have been tasked with evaluating a new mobile banking **app. What are some specific questions you would ask to determine if it meets the goals of a usability evaluation?**

- **Effectiveness:** "Can the user successfully transfer money without assistance?"
    
- **Efficiency:** "How many taps does it take to check the balance?"
    
- **Satisfaction:** "Does the user feel secure and confident using the app?"
    

**4. What is the difference between a heuristic and a design principle? Find an example of each.**

- **Design Principle:** High-level, abstract guidance.
    
    - _Example:_ "Consistency."
        
- **Heuristic:** A specific, empirical rule of thumb used for evaluation (often a checklist).
    
    - _Example:_ Nielsen’s Heuristic #4: "Users should not have to wonder whether different words, situations, or actions mean the same thing."
        

## Week 8: HCI Design Rules, Guidelines & Evaluation Techniques (2)

**1. Imagine you are evaluating a new fitness tracking app. What is one specific question you would ask to evaluate each of the five criteria?**

- **Efficiency:** How long does it take to log a workout?
    
- **Learnability:** Can a new user find the "Start Run" button in under 10 seconds?
    
- **Memorability:** If the user stops using the app for a week, can they remember how to check their history without relearning?
    
- **Errors:** How often do users accidentally discard a workout instead of saving it?
    
- **Satisfaction:** On a scale of 1-5, how motivating is the interface?
    

**2. A company wants to evaluate a new, revolutionary smart thermostat. Which evaluation method would you recommend (expert analysis or user participation) and why?**

- **Recommendation:** **User Participation (Field Study).**
    
- **Why:** A thermostat is highly context-dependent. Expert analysis in a lab cannot replicate the environmental factors (cold/hot rooms), the physical placement in a hallway, or the erratic schedules of a real family.
    

**3. Conduct a heuristic evaluation of a common website (e.g., a university portal). Identify three usability problems and recommend how to fix them.**

- **Problem 1:** Search bar returns irrelevant results. (Violates: Flexibility and efficiency of use). _Fix:_ Improve search indexing.
    
- **Problem 2:** Error messages say "Error 503". (Violates: Help users recognize, diagnose, and recover from errors). _Fix:_ Change to "Server busy, please try again."
    
- **Problem 3:** Different fonts on different pages. (Violates: Consistency and standards). _Fix:_ Standardize CSS styles.
    

**4.** Describe how you could use the think-aloud protocol to evaluate a microwave's user interface. What are the **pros and cons?**

- **Method:** Ask a user to defrost a chicken. Ask them to speak every thought: "I am looking for the defrost button... I see a snowflake icon... I am pressing it... nothing happened... oh, I have to enter weight first."
    
- **Pros:** Reveals the _why_ behind errors (user mental model vs system model).
    
- **Cons:** Unnatural interaction; thinking aloud slows down the task and may alter performance.
    

## Week 9: HCI Models and Theories (1)

**1.** Use the GOMS model **to analyse the task of sending a text message on a smartphone.**

- **Goal:** Send "Hello" to Mom.
    
- **Operators:** Unlock phone, Tap Message App, Tap New Message, Type "Mom", Tap "Mom" in list, Type "Hello", Tap Send.
    
- **Methods:** Could use voice dictation OR virtual keyboard.
    
- **Selection Rules:** If in a library, use keyboard. If driving, use voice.
    

**2.** Choose an application you frequently use. Are there any commands or menu options that feel like a foreign language? How could **the designer improve the "linguistics" of the interface?**

- **App:** Photoshop or Advanced Editors.
    
- **Issue:** Terms like "Rasterize," "Kerning," or "Gamut."
    
- **Improvement:** Use **Metaphors** or plain English descriptions. Instead of "Rasterize," use "Convert to Image." Or provide tooltips explaining the term on hover.
    

**3.** According to Fitts' Law, why is a **large "send" button at the bottom of a mobile screen more efficient than a small one in the top corner?**

- **Fitts' Law Formula:** Time to acquire target depends on Distance (D) and Size (W).
    
- **Analysis:** A button at the bottom is closer to the thumb (Low D) and if it spans the width of the screen, it is effectively very large (High W). A small button at the top requires a reach (High D) and precision (Low W), making it slower and more error-prone.
    

**4.** How might a cognitive architecture be used to simulate a user's thought process when they are learning to use a new, complex software program for **the first time?**

- Simulations like ACT-R can model how humans retrieve facts from memory. It can predict:
    
    - How many times the user will forget the location of a menu item.
        
    - How long it takes to transfer knowledge from short-term to long-term memory.
        
    - This helps designers simplify complex workflows before testing with real humans.
        

## Week 10: HCI Models and Theories (2)

**1.** Conduct a Hierarchical Task Analysis (HTA) for the task "Make a video call" on **a smartphone, identifying the goals, sub-tasks, and operations.**

- **0. Make Video Call**
    
    - **1. Access Contact**
        
        - 1.1 Unlock phone.
            
        - 1.2 Open Phone/WhatsApp App.
            
        - 1.3 Search for Name.
            
    - **2. Initiate Call**
        
        - 2.1 Select Contact.
            
        - 2.2 Tap Video Icon.
            
    - **3. Manage Connection**
        
        - 3.1 Wait for answer.
            
        - 3.2 Adjust Volume/Camera angle.
            

**2. Think about an online tool you use for collaboration (e.g., Google Docs, Slack). How has this tool changed the way you communicate with others, and what are the advantages and disadvantages compared to face-to-face communication?**

- **Tool:** Slack/Google Docs.
    
- **Change:** Shift from Synchronous (Same time) to Asynchronous (Different time) communication.
    
- **Advantages:** Persistent record (history), ability to edit before sending, allows deep work without interruption.
    
- **Disadvantages:** Loss of non-verbal cues (tone, facial expression), leading to misunderstandings. "Gulf of Evaluation" regarding the emotional state of the colleague.
    

**3.** As computing becomes more ubiquitous, what are some of the new challenges for designers in terms of privacy **and data security?**

- **Passive Collection:** Ubiquitous computing (IoT) collects data without explicit user interaction (e.g., a smart fridge tracking diet).
    
- **Challenge:** How to inform the user they are being recorded without annoying them? How to provide "consent" mechanisms on devices that have no screens?
    

**4.** What do you think is the "next big thing" in HCI? Justify your answer based on the concepts of paradigms and the future of **interaction discussed in the text.**

- **Prediction:** **Brain-Computer Interfaces (BCI)** or **Augmented Reality (AR) Overlay.**
    
- **Justification:** The history of HCI moves closer to the user: Mainframe (Room) -> PC (Desk) -> Smartphone (Pocket) -> Wearable (Wrist). The next logical step is integration with the body (Eyes/Brain), removing physical I/O devices entirely to reduce the Gulf of Execution to zero.