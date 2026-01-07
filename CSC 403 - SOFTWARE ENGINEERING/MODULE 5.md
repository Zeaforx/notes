# Software Engineering Student Notes

## I. Software Components

### The Five Criteria for a Component

According to Szyperski and Messerschmitt, a software component must meet these five criteria to fulfill its role in engineering:

1. **Multiple-use**: It must be designed for reuse in different contexts or applications.
    
2. **Non-context-specific**: It should not depend on a specific environment or system state to function.
    
3. **Composable with other components**: It must be able to "plug in" and interact with other parts of a system seamlessly.
    
4. **Encapsulated**: It is "non-investigable" through its interfaces (a black box); the internal logic is hidden.
    
5. **Unit of independent deployment**: It can be versioned and installed as a standalone entity.
    

### A Simpler Definition

A component is an **object written to a specification** (like COM or Java Beans).

- **Definition**: A modular, deployable part of a system that encapsulates its contents and provides services through interfaces.
    
- **Importance**: Adhering to a specification is what allows different objects to gain features like **reusability** and **interoperability**, meaning they can work together regardless of who built them.
    

### Technical Implementation (IDL and Serialization)

Components often take the form of objects adhering to an **Interface Description Language (IDL)** so they can exist autonomously from other components.

- **Serialization (Marshaling)**: The process of turning a component or its interface into a **bit stream**.
    
- **Importance**: Serialization is critical when a component needs to be accessed or shared across different network links or execution contexts.
    
- **Analogy**: Think of **Serialization** like **IKEA furniture**. The component is the full desk; serialization "flat-packs" it into a box (bit stream) so it can be shipped easily over the network, and then it is reassembled (deserialized) once it reaches its destination.
    

### Requirements for Effective Reuse

Creating a component that others can actually use requires significant effort. A reusable component needs:

- **a) Full Documentation**: Comprehensive guides on how the component works.
    
- **b) Thorough Testing**: Ensuring reliability across many use cases.
    
- **c) Robust Input Validity Checking**: Preventing the component from crashing when given bad data.
    
- **d) Useful Error Messages**: Helping developers identify issues quickly.
    
- **e) Awareness of Unforeseen Uses**: Designing for flexibility rather than just one specific task.
    
- **f) Compensation Mechanism**: A system to reward developers for the substantial extra effort required to make code "reusable."
    

## II. Component-Based Software Development (CBSE)

### The Essentials of CBSE

**CBSE** (also known as Component-Based Software Engineering) is a development process focused on the composition of reusable, standardized components.

- **Independent Components**: A clear separation ensures one component can be replaced without breaking the rest of the system.
    
- **Component Standards**: These rules facilitate integration, allowing components written in different languages to work together.
    
- **Middleware**: The software layer that provides the "glue" or infrastructure for components to communicate.
    
- **Development Process**: The entire methodology must be adapted to prioritize searching for and integrating existing components over writing new code.
    

### Problems of CBSE

1. **Component Trustworthiness**: Since components are "black boxes" and source code is often hidden, they could contain a **Trojan Horse** (hidden malicious code).
    
2. **Component Certification**: There is a constant need for independent third parties to verify that components actually do what they claim.
    
3. **Emergent Property Prediction**: Because components are opaque, it is difficult to predict how the overall system will behave once they are combined.
    
    - _Analogy_: Like mixing two different chemicals; you know the properties of each individual liquid, but the **emergent property** (a sudden change in temperature or a chemical reaction) only appears once they are mixed.
        
4. **Requirements Trade-offs**: You may have to compromise on your ideal design because the available components don't fit your needs perfectly.
    
    - _Scenario_: You want a car with a 1000-mile range, but the only available battery component provides 300 miles. You **trade off** your high-range requirement to use the available, tested component.
        

### Component Characteristics

Reusable components should be **Standardised, Independent, Composable, Deployable,** and **Documented**.

### Two Critical Characteristics of a Reusable Component

1. **Independent Executable Entities**: They are ready to run and do not require the user to have the original source code or re-compile the program.
    
2. **Interface-Based Services**: The services provided are only accessible through a strictly defined interface.
    

### Component Interfaces (The 'Requires' vs. 'Provides' model)

- **Provides Interface**: Defines the services that the component offers to other parts of the system.
    
- **Requires Interface**: Defines what the component needs from its environment to function.
    
- **Real-World Example (Data Collector)**:
    
    - A **Data Collector** component _provides_ services such as "add sensor," "start sensor," and "report."
        
    - However, it _requires_ a "Sensor Management" interface to be present in the system to actually talk to the hardware.
        

### Types of Components

- **Run-time software component**: Components that exist while the system is executing.
    
- **Business component**: Logic that handles a specific business task (e.g., "Payroll Calculation").
    
- **Qualified, Adapted, and Update components**: Specialized versions used to fit specific requirements or update existing systems.
    

## III. Programming Languages and Software Development

**Programming Languages** are the foundation of all development activities. In modern engineering, we focus on **High-Level Languages (HLL)** and **Object-Oriented Programming (OOP)**.

- **Importance**: OOP is vital for reuse because classes and methods are designed to be modular and easily repurposed in new projects.
    

## IV. Software Development Methodology

A **Methodology** involves breaking the development process into distinct phases for better management.

### Waterfall Model/Method

A linear, sequential flow: Planning → Analysis → Design → Implementation → System.

- **Importance**: Requirements are frozen early, which minimizes "scope creep" (uncontrolled changes).
    
- **Analogy**: Like **building a bridge**. You cannot decide to move the bridge's location once the concrete pillars are poured; everything must be perfect in the design phase before construction starts.
    

### Prototype

This technique performs analysis, design, and implementation concurrently and repeatedly.

- **Importance**: It provides a fast-paced environment where users can see and test a "working model" early on.
    
- **Scenario**: A developer creates a "clickable" but non-functional version of a mobile app to show a client. The client gives feedback, and the developer changes the layout immediately—this is **prototyping**.
    

### Parallel Development Technique

The project is divided into subprojects that are designed and implemented at the same time and integrated later.

- **Importance**: It significantly shortens the time between the start of the project and the final delivery.
    
- **Analogy**: Like **cooking a big holiday meal**. One person mashes the potatoes while another roasts the turkey. They both finish their "subprojects" simultaneously to serve the full "System" (dinner) much faster.
    

## V. Software Testing

### System Testing Phases

Before final delivery, software undergoes three key phases:

1. **Alpha Testing**: Conducted by the internal team at the developer's site.
    
2. **Beta Testing**: Performed by a selected group of real-world users in their own environment.
    
3. **Acceptance Testing**: The final check performed by the customer to ensure the product meets all requirements before installation.
    

### Testing Tools

The goal of testing is to **make the application fail**. By trying every possible combination of data, engineers ensure the software is robust.

- **Tools**: IDEs like **NetBeans**, **VS Code**, and **Visual Studio** come with built-in testing suites to automate this process.
    

### How to Debug with XDebug and NetBeans

**Debugging** is the act of fixing errors (bugs) found during testing.

- **XDebug**: A powerful tool (often included in XAMPP) that acts as a "debugger."
    
- **Implementation**: When configured with an IDE like NetBeans, it allows developers to pause their code and see exactly what is happening inside the computer's memory.
    

## VI. Software in Modern Society

Software is the invisible force ruling modern society, from government and transportation to manufacturing.

- **The Driver**: Competition and the "insatiable appetite" for better products drive the expansion of software systems.
    
- **Final Thought**: Without software, the modern conveniences we take for granted would be impossible to maintain.