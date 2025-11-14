# Week 4: HCI Design Principles (1) - Interaction Design Fundamentals

## a. What is Interaction Design (IxD)?

**Objective 1:** Define interaction design and its role in software development.

### Core Definition

- **Interaction Design (IxD):** This is the practice of designing **how a user interacts with a product**. It's not just about how it looks, but about how it _behaves_ and _feels_ to use.
    
- **The Goal:** To design interactive products that support how people communicate and interact in their daily lives. It defines the _entire user experience_, from the first click to the last.
    

### IxD vs. Visual Design vs. Usability

This table helps clarify the differences:

|   |   |   |
|---|---|---|
|**Discipline**|**Focus Question**|**Real-World Example (e.g., a "Sign Up" button)**|
|**Visual Design**|"Does it look good?"|Is the button blue or green? Is the font readable and on-brand? Are the corners rounded?|
|**Interaction Design (IxD)**|"How does it work?"|What happens when the user clicks it? Does a loading spinner appear? What error message shows if the password is too weak? Does the button change to "Success!" after?|
|**Usability**|"Can the user achieve their goal easily?"|Is the button easy to find? Can the user sign up in 20 seconds, or does it take 5 minutes? How many users abandon the form?|

### The Core Goal: Bridging the "Gaps" (Don Norman)

A good interaction designer's main job is to minimize two key problems for the user:

1. **The Gulf of Execution:**
    
    - **What it is:** The gap between what the user _wants to do_ and the actions the system _requires_ them to take.
        
    - **User's Thought:** "I want to save my document, but I have no idea how."
        
    - **Real-World Example:** On a confusing TV remote, you want to change the input to "HDMI 1." You have to press "Menu," navigate to "Source," scroll past 5 options, and then press "Select." This is a _wide_ gulf.
        
    - **How IxD Bridges It:** A dedicated "Input" button on the remote (a clear **affordance**) that directly shows the input list.
        
2. **The Gulf of Evaluation:**
    
    - **What it is:** The difficulty the user has in figuring out the system's _current state_ and whether their action was _successful_.
        
    - **User's Thought:** "I clicked 'Submit,' but... did it work? Is it loading? Is it broken?"
        
    - **Real-World Example:** You upload a file to a website. After you click "Upload," the page just sits there. You have no idea if it's working or if you should click again. This is a _wide_ gulf.
        
    - **How IxD Bridges It:** Providing immediate and meaningful **feedback**, such as a progress bar, a spinning icon, and a clear "File Uploaded Successfully!" message.
        

> **Key Terms:**
> 
> - **Affordance:** A visual cue that suggests what an object can do. A button _looks like_ it can be pushed. A door handle _affords_ pulling.
>     
> - **Feedback:** The system's response to a user's action, which communicates the result.
>     

## b. The Software Design Process (Iterative & User-Centric)

Unlike the old "Waterfall" model (where each step is finished before the next begins), HCI design is a **continuous cycle**.

The four main phases are:

1. **Requirements:**
    
    - **Goal:** Establish what is needed.
        
    - **Methods:** Don't just guess! Observe users with existing systems. Conduct interviews, surveys, and observations to find out what different users _really_ need (not just what they _say_ they want).
        
2. **Analysis:**
    
    - **Goal:** Make sense of all the data from the requirements phase.
        
    - **Methods:** Organize interview notes, identify key issues, and find patterns in user behavior. This helps communicate the core problems to the design team.
        
3. **Design:**
    
    - **Goal:** Move from "what" is needed to "how" it will work.
        
    - **Methods:** This is where you apply cognitive models, create user flows, and sketch out interfaces. You must design for _many_ different kinds of users, not just yourself.
        
4. **Implementation & Deployment:**
    
    - **Goal:** Build and deliver the product.
        
    - **Methods:** Writing code, building hardware, writing user manuals.
        
    - **The Iteration Loop:** This is the most critical part. You build a **prototype** (a simple, testable version), give it to real users, and _watch what happens_. You find errors, get feedback, and then go _back_ to the design phase to fix them. You repeat this loop until the product is ready.
        

## c. Navigation Structures in Interaction

This is about how a user _moves through_ your system.

1. **Local Structure (Goal-Seeking):**
    
    - **What it is:** The interaction with elements on a _single screen_ to achieve a small goal.
        
    - **Think:** Buttons, links, toolbars, and menus.
        
    - **Example:** In a word processor, the "toolbar" with **Bold**, _Italic_, and `Underline` buttons is the local structure. You use it to act on the text right in front of you.
        
2. **Global Structure (Information Architecture):**
    
    - **What it is:** The overall map of the system—how all the different screens, pages, and states are connected.
        
    - **Think:** The main site navigation, the hierarchy, the overall flow.
        
    - **Example:** On an e-commerce website, the global structure is the main menu bar: `Home | Men | Women | Kids | Sale`. This organizes the entire site into logical groupings.
        

**The Big Challenge:** Different users have different _mental models_ and _vocabularies_.

- **Example:** One user might look for "shipping costs" under a "Help" section, while another expects to see it in the "Checkout" process. A good designer uses **user research** (like card sorting) to create a hierarchy that makes sense to the _users_, not just to the designers.
    

## d. Screen Design and Layout

How do you arrange elements on the screen?

**Core Principle: "Form Follows Function"**

- **What it means:** The design (form) should be driven by what the user needs to _do_ (function).
    
- **Real-World Example:** On a streaming app's "Now Playing" screen, the _primary function_ is to play/pause. Therefore, the _form_ should be a large, centrally-located play/pause button that is easy to hit, not a tiny icon in a corner.
    

**A 4-Step Process for Screen Design:**

1. **Ask:** What is the user _actually doing_ on this screen? (e.g., "Comparing two products," "Filling out a form," "Reading an article").
    
2. **Think:** What information is required to do that? In what _order_ will they need it? What do they need to _compare_?
    
3. **Design:** Let the answers from "Ask" and "Think" drive your layout.
    
4. **Test:** Create a prototype (even a simple paper sketch) and test it with users. Don't wait until after it's coded to find out the layout is confusing!
    

## e. User Focus

**Objective 2:** Explain the principle of user focus and the role of user research.

**Core Principle:** All design decisions **must** be informed by the user's needs, goals, and limitations.

> **Warning:** If you design for yourself, you are designing for an expert user who already knows how it's "supposed" to work. This is the #1 trap for new designers.

### Key Components of User Focus

1. **Understanding the User (Personas):**
    
    - **What it is:** Creating **Personas**—fictional, representative models of your typical users.
        
    - **Why?** It makes the user "real." It stops debates like "I like this design" and changes them to "Would _'Sarah the Busy Student'_ find this useful?"
        
    - **Mini-Example Persona:**
        
        - **Name:** 'Commuter Carl'
            
        - **Who:** A 45-year-old marketing manager.
            
        - **Context:** Uses our news app on a crowded train for 20 minutes each morning.
            
        - **Needs:** One-handed navigation, large fonts, and the ability to save articles for offline reading.
            
2. **Understanding the Context of Use:**
    
    - **What it is:** Analyzing _where_, _when_, and _why_ the system is used.
        
    - **Example (from material):** Designing a navigation app for a _driver_ (glanceable info, big buttons, voice commands) is completely different from a _desktop banking portal_ (detailed info, high security, keyboard/mouse input).
        
    - **Another Example:** An app for a _factory worker_ might need to be usable with gloves and have loud audio alerts, while an app for a _librarian_ must be silent and have high-contrast text.
        

### The Role of User Research

User research is how you move from _assumptions_ to _facts_.

- **Qualitative Methods (Answers "Why?"):**
    
    - **Interviews:** One-on-one conversations to understand a user's motivations, pains, and thought processes.
        
    - **Ethnographic Studies:** Observing users in their _natural environment_ (e.g., watching a chef use a recipe app in their actual kitchen). This is excellent for finding workarounds or "tacit" requirements they would never think to tell you about.
        
- **Quantitative Methods (Answers "How Many?"):**
    
    - **Surveys:** Gathers data from a large group of users.
        
    - **A/B Testing:** Showing two versions of a design to different users to see which one performs better (e.g., does the red button or the green button get more clicks?).
        
    - **System Logs / Analytics:** Looking at data to see what features users _actually_ use, where they drop off, and what errors they encounter.
        

## f. Scenarios

**Objective 3:** Write effective scenarios to guide the design of an interactive system.

### What is a Scenario?

A **Scenario** is an informal narrative or story that describes a specific instance of a user (a **Persona**) interacting with a system to achieve a specific **Goal**.

- **Why they are Essential (Design Glue):**
    
    - **Grounds the Team:** They keep the design focused on real-world human experience, not just abstract features.
        
    - **Validates the Design:** They are the first "test case." The team can "walk through" a design sketch and see if it actually works for the user in the story.
        

### Required Elements of a Good Scenario

1. **Actor:** The user, often a named Persona (e.g., "Commuter Carl").
    
2. **Goal:** The explicit outcome the user wants (e.g., "save an article to read later").
    
3. **Context:** The environmental or situational factors (e.g., "on a crowded train," "distracted," "using one hand on a small screen").
    
4. **Steps:** A step-by-step narration of the user's actions and the system's expected responses.
    

### Simple Example: Scenario for a Pizza App

- **Actor:** 'Busy Brian' (Persona for a user who values speed).
    
- **Goal:** Order his "usual" pizza as fast as possible.
    
- **Context:** It's 7 PM on a Friday. He's at home, distracted by a football game on TV, and using his smartphone.
    
- **Steps:**
    
    1. Brian opens the pizza app.
        
    2. The app homepage immediately shows a "Re-order Your Usual" button (based on his history).
        
    3. Brian taps this button.
        
    4. A confirmation screen appears with his usual order (Large Pepperoni) and his saved address/payment.
        
    5. He taps "Confirm Order."
        
    6. The app shows a "Success! Your pizza is on its way" screen with an estimated delivery time.
        

## g. Navigation Design

This is the practice of structuring and labelling content to help users find what they are looking for and understand **where they are**. It's a key part of the system's **Information Architecture (IA)**.

- **Goal:** Prevent the user from feeling "Lost in Hyperspace"—that feeling of confusion where you don't know your current location in an app or the path to your target.
    

### Key Principles of Good Navigation

1. **Consistency:**
    
    - The primary navigation (like the top menu or side-bar) must remain in the same place and behave the same way on _every single page_.
        
    - **Example:** On Amazon, the "Shopping Cart" icon is _always_ in the top-right corner. It doesn't move.
        
2. **Clarity of Labels:**
    
    - Use precise, simple, user-centric language. Avoid internal jargon.
        
    - **Example:** Use "My Account" or "Profile" instead of "User Configuration Module." Use "Contact Us" instead of "Syn-8 Corporate Inquiry."
        
3. **Feedback (Indicating Location):**
    
    - The user must _always_ know where they are.
        
    - **Breadcrumbs:** A trail of links showing the path from the homepage to the current page.
        
        - `Home > Men's Clothing > Shoes > Hiking Boots`
            
    - **Highlighting / Active State:** The current menu item should be visually different (e.g., bolded, underlined, or a different color) to show the user "You are here."
        

## h. Prototyping Techniques

**Objective 4:** Describe and compare different prototyping techniques.

A **Prototype** is a tangible, testable representation of a design idea. Its purpose is to get feedback and validate ideas _before_ committing time and money to building the final product.

**Fidelity:** Refers to how closely the prototype resembles the final product (in terms of visuals, content, and interactivity).

### Comparison of Prototyping Techniques

|   |   |   |   |
|---|---|---|---|
|**Technique**|**Fidelity**|**Description**|**Primary Purpose (When to Use)**|
|**Sketching / Paper Prototype**|**Low**|Hand-drawn screens. The designer "plays computer" by swapping paper sketches as the user "taps" on them.|**Testing big-picture ideas.** Very fast, very cheap. Perfect for testing the _conceptual flow_ and _basic layout_ in the earliest stages.|
|**Storyboarding**|**Low**|A comic-strip-like sequence of drawings. Focuses on the user's emotion, environment, and experience _over time_.|**Testing the Context of Use.** Helps the team understand the user's _motivation_ and _problem_ before designing a solution.|
|**Wireframes**|**Medium**|Digital, black-and-white mockups (e.g., using tools like Balsamiq or Figma). Focuses on _structure_, _content placement_, and _interaction zones_.|**Defining Information Architecture.** Perfect for agreeing on _what_ goes on each page and _how_ pages connect, without getting distracted by colors or fonts.|
|**High-Fidelity (Hi-Fi) Mockup**|**High**|A highly detailed, interactive model (using tools like Figma or Sketch) that looks and feels like the final product. No "real" code.|**Final usability testing.** Used to test specific _micro-interactions_ (like animations) and evaluate the _visual design_ before handing it off to developers.|

## i. Illustrative Scenarios (Application Cases)

These examples show how the principles are applied to real-world problems.

### Case 1: Complex Task (Online Flight Booking)

- **Goal:** Book a one-way, non-stop flight (Lagos to London) using loyalty points and including one checked bag.
    
- **Actor:** Amara (38), a frequent flyer (Persona) who is efficient and expects good service.
    
- **Context:** Multitasking at her work computer.
    
- **Analysis of Interaction:**
    
    - **User Action:** Amara inputs LOS -> LHR and selects "One-Way."
        
    - **System Response:** Instantly suggests airport names. (**Principle: Feedback**)
        
    - **User Action:** Checks "Pay with Points" and "1 Checked Bag."
        
    - **System Response:** The form validates these options _immediately_. (**Principle: Feedback / Bridging Gulf of Evaluation**)
        
    - **Why this is good IxD:** The system allows Amara to input all her complex criteria (points, bag) at the _start_ of the search, not as filters _after_ the search. This massively reduces her effort. (**Principle: Bridging Gulf of Execution**)
        

### Case 2: User Research (New Social Networking Site)

- **Task:** How would you use research to make a new social media app user-focused?
    
- **Methods:**
    
    1. **Ethnographic Studies:** _Observe_ users in their real lives. You might find that people _say_ they want privacy, but _actually use_ four different apps to manage different social circles. This uncovers **tacit requirements** (needs they can't even articulate).
        
    2. **High-Fidelity Prototype Testing:** Social media is all about _feel_ and _behavior_. A Hi-Fi prototype lets you test: Is the "Like" feedback satisfying? Is sharing intuitive? This validates the core interaction flow _before_ coding.
        
    3. **Competitive Heuristic Evaluation:** Systematically review competing apps (like Instagram, TikTok) against established usability rules (like "Nielsen's 10 Heuristics"). This finds common pitfalls and ensures your new site avoids them, achieving a higher baseline of quality from the start.
        

### Case 3: Navigation Redesign (Poor E-commerce Site)

- **Task:** Fix a site where finding "Men's waterproof hiking boots" is too hard.
    
- Old, Bad Navigation (6 Clicks):
    
    Shop → Men's → Footwear → Boots → Hiking → Filter: Waterproof
    
- **Proposed New, Good Navigation (3 Clicks):**
    
    1. **Primary Nav (Top Bar):** `NEW ARRIVALS` | `MEN` | `WOMEN` | `SALE`
        
    2. **User Action:** Hovers/taps `MEN`.
        
    3. **Dropdown Menu:**
        
        - `CLOTHING`
            
        - `FOOTWEAR` → (User clicks this)
            
        - `ACCESSORIES`
            
    4. **User Action:** Lands on the `FOOTWEAR` page.
        
    5. **Faceted Filtering (Left Sidebar):**
        
        - `[ ] Boots` (User clicks this)
            
        - `[x] Waterproof` (User clicks this)
            
- **Justification (Why it's Better):**
    
    - **Clarity:** Replaced vague "Shop" with direct categories.
        
    - **Reduced Gulf of Execution:** Slashed the number of clicks/pages from 6 to 3.
        
    - **Better IA:** Introduced **Faceted Filters**, which are user-friendly controls that allow users to _filter_ by multiple attributes (category, feature, brand) at once, rather than digging through deep, rigid hierarchies.
        

### Case 4: Prototyping (Water Intake Mobile App)

- **Task:** Test a new app to track daily water intake _before any code is written_.
    
- **Techniques:**
    
    1. **Paper Prototyping (Low-Fidelity):**
        
        - **Design:** Sketch the main dashboard and the "Log Water" button on paper.
            
        - **Testing Goal:** Test the _core functional flow_: logging water. The #1 requirement is speed.
            
        - **Method:** Give a user the paper prototype in a distracting environment and ask them to "log a glass of water." Can they do it in under 3 seconds? This confirms the layout works _before_ you even think about colors.
            
    2. **Storyboarding (Low-Fidelity):**
        
        - **Design:** A 6-panel comic: (1) User wakes up. (2) User drinks coffee, forgets water. (3) App sends a notification. (4) User taps notification. (5) User logs water (links to the paper prototype flow). (6) User feels satisfied.
            
        - **Testing Goal:** Test the _Context of Use_ and _motivation_. Does the notification trigger make sense? Does this flow fit into a user's _actual day_? This validates the _problem_ and the _motivational loop_, not just the UI.