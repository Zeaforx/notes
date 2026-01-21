# Student Study Notes: Concepts of Programming Languages

## Chapter 1: Preliminaries

**Objective:** These notes are designed to transform raw textbook concepts into a structured, easy-to-understand study guide. Use these notes to master the fundamental reasons for studying programming languages, the criteria for evaluating them, and the history of their design and implementation.

### 1.1 Reasons for Studying Concepts of Programming Languages

Understanding the underlying concepts of programming languages is crucial for computer scientists, not just for designing languages, but for becoming better software developers.

- **Increased capacity to express ideas**
    
    - **Define:** The ability to conceptualize and implement complex structures and algorithms is directly tied to the expressive power of the language you "think" in.
        
    - **Explain:** Just as natural language limits the complexity of abstract thought (the Sapir-Whorf hypothesis), a programmer's understanding of limited language constructs limits the algorithms they can construct. Learning new concepts expands your "mental vocabulary."
        
    - **Example:** A programmer who only knows C (an imperative language) might struggle to conceptualize a complex recursive solution that would be trivial for a programmer who understands Scheme (a functional language), even if they are writing the final code in C.
        
- **Improved background for choosing appropriate languages**
    
    - **Define:** The capability to critically evaluate and select the best language for a specific task rather than simply using the one you know best.
        
    - **Explain:** Many programmers use languages simply because they are familiar with them. A broad background allows you to match the features of a language (e.g., strong string manipulation) to the requirements of the project (e.g., text processing).
        
    - **Analogy:** If the only tool you have is a hammer, everything looks like a nail. Studying language concepts gives you a full toolbox (screwdrivers, wrenches, saws) so you can pick the right tool for the job.
        
- **Increased** ability to learn **new languages**
    
    - **Define:** The skill to transfer knowledge from one language to another based on shared fundamental concepts.
        
    - **Explain:** Languages are rarely unique; they share underlying concepts like data abstraction, object-oriented programming, or recursion. Once you understand the _concept_ (e.g., a "Class"), learning the syntax for it in a new language (Java vs. C#) is trivial.
        
    - **Example:** If you understand the concept of **Object-Oriented Programming** in C++, learning Java is primarily a matter of learning new syntax, rather than learning how to program from scratch.
        
- **Better understanding of the significance of implementation**
    
    - **Define:** Knowledge of how language constructs are actually executed by the computer (e.g., memory management, stack usage).
        
    - **Explain:** Understanding implementation allows a programmer to use the language more intelligently and efficiently. It helps in finding bugs and understanding performance bottlenecks.
        
    - **Example:** A programmer who understands how recursion is implemented (using the call stack) will understand why a recursive function with no base case causes a "Stack Overflow" error.
        
- **Better** use of languages **that are already known**
    
    - **Define:** Unlocking the full potential of a language you already use by understanding its obscure or advanced features.
        
    - **Explain:** Many languages are vast and complex. By studying general language concepts, you may recognize and utilize features in your current language that you previously ignored or didn't understand.
        
    - **Example:** A Python programmer might ignore "decorators" or "generators" until they study the general concepts of higher-order functions and lazy evaluation.
        
- **Overall advancement of computing**
    
    - **Define:** The collective improvement of the software industry through informed decision-making.
        
    - **Explain:** If those in positions of power (managers, senior devs) understand language concepts, they are more likely to adopt superior modern languages rather than sticking to outdated ones due to inertia.
        
    - **Example:** The persistence of **Fortran** over **ALGOL 60** in the 1960s is often cited as a failure of the industry to appreciate superior language design (ALGOL's block structure) due to a lack of conceptual understanding.
        

### 1.2 Programming Domains

Different problems require different tools. Programming languages are often designed for specific "domains" or application areas.

#### 1.2.1 Scientific Applications

- **Define:** Applications requiring complex mathematical calculations, large numbers of floating-point arithmetic, and array manipulations.
    
- **Characteristics:** Focus on efficiency and simple data structures (arrays, matrices).
    
- **Example Language:** **Fortran** (Formula Translation). It was the first language for this domain and remains in use because of its extreme efficiency in number crunching.
    

#### 1.2.2 Business Applications

- **Define:** Systems focused on producing reports, storing data, and performing decimal arithmetic.
    
- **Characteristics:** Needs precise decimal numbers (to avoid rounding errors in money) and character data handling.
    
- **Example Language:** **COBOL** (Common Business Oriented Language). It looks like English and is designed for generating elaborate reports and managing business data.
    

#### 1.2.3 Artificial Intelligence

- **Define:** Applications involving symbolic computation rather than numeric computation.
    
- **Characteristics:** Manipulates symbols (names/words) using linked lists rather than arrays. Often requires code that can create and execute other code during runtime.
    
- **Example Language:** **LISP** (List Processing) was the first. Modern AI often uses Python, though traditionally **Prolog** (logic programming) and LISP were dominant.
    

#### 1.2.4 Systems Programming

- **Define:** Writing the software that runs the computer itself (operating systems, device drivers, compilers).
    
- **Characteristics:** Must be fast (efficient) and allow low-level access to hardware. It essentially replaces Assembly language.
    
- **Example Language:** **C**. The UNIX operating system is written in C, making it the standard for systems programming.
    

#### 1.2.5 Web Software

- **Define:** A diverse collection of languages used to support the World Wide Web.
    
- **Characteristics:** Ranges from markup (formatting) to scripting (dynamic behavior) to general-purpose logic.
    
- **Example Languages:**
    
    - **Markup:** HTML (HyperText Markup Language).
        
    - **Scripting:** JavaScript (run on the client/browser), PHP (run on the server).
        
    - **General Purpose:** Java.
        

### 1.3 Language Evaluation Criteria

How do we decide if a language is "good"? We use specific criteria: **Readability, Writability, Reliability, and Cost.**

#### 1.3.1 Readability

> **Definition:** The ease with which programs can be read and understood. This is critical for maintenance (which is the most expensive part of the software life cycle).

- **1.3.1.1 Overall Simplicity**
    
    - **Define:** A language should have a manageable set of constructs.
        
    - **Explain:** If a language is too large, programmers might only learn a subset. If two programmers use different subsets, they cannot read each other's code.
        
    - **Feature Multiplicity:** Having multiple ways to do the same thing (e.g., `count++`, `count = count + 1`, `count += 1`). This is generally bad for readability.
        
    - **Operator Overloading:** When one symbol has multiple meanings. It is good if intuitive (`+` for integer and float addition) but bad if complex (users defining `+` to subtract vectors).
        
- **1.3.1.2 Orthogonality**
    
    - **Define:** A small set of primitive constructs can be combined in a relatively small number of ways, and every possible combination is legal and meaningful.
        
    - **Explain:** No "special cases" or exceptions. If you can use a variable here, you should be able to use _any_ data type here.
        
    - **Analogy:** **LEGOs** are orthogonal; any brick fits on any other brick. **Jigsaw puzzles** are non-orthogonal; specific pieces only fit in specific spots.
        
    - **Example of Lack of Orthogonality:** In C, a function can return a `struct` (record), but it cannot return an `array`. This is an arbitrary exception that confuses the learner.
        
- **1.3.1.3 Data Types**
    
    - **Define:** The presence of adequate facilities for defining data types.
        
    - **Explain:** A language with a specific data type (like `Boolean` for true/false) is more readable than one that forces you to use a numeric `1` or `0` as a flag.
        
- **1.3.1.4 Syntax Design**
    
    - **Define:** The form of the language elements.
        
    - **Special Words:** Using clear words like `while`, `class`, `for`.
        
    - **Form and Meaning:** The appearance of a statement should suggest its purpose.
        
    - **Bad Example:** The UNIX command `grep` does not intuitively suggest "search for a string."
        

#### 1.3.2 Writability

> **Definition:** The ease with which a language can be used to create programs for a chosen problem domain.

- **Simplicity and Orthogonality:** (See Readability). If a language has fewer rules and exceptions, it is easier to learn and write.
    
- **Support for Abstraction:**
    
    - **Process Abstraction:** Using a subprogram (function) to hide the details of a sort algorithm.
        
    - **Data Abstraction:** Using a `binary tree` class rather than managing three separate arrays of integers manually.
        
- **Expressivity:**
    
    - **Define:** Having convenient and concise ways of specifying computations.
        
    - **Example:** `count++` is more expressive (convenient) than `count = count + 1`.
        

#### 1.3.3 Reliability

> **Definition:** A program is reliable if it performs to its specifications under all conditions.

- **Type Checking:** Checking for type errors (e.g., passing a string to a math function). **Compile-time** checking (Java) is more reliable than **Run-time** checking.
    
- **Exception Handling:** The ability to intercept run-time errors (like dividing by zero) and fix them without crashing.
    
- **Aliasing:** Having two or more distinct names for the same memory cell. This is **dangerous** for reliability because changing one variable changes the other without warning.
    
- **Readability/Writability:** If a code is hard to read or write, it is more likely to contain bugs.
    

#### 1.3.4 Cost

> **Definition:** The total cost includes training, writing, compiling, executing, and maintaining.

- **Training Cost:** High if the language is complex.
    
- **Creation Cost:** High if the language is not expressive (low writability).
    
- **Compilation Cost:** High if the compiler attempts too much optimization.
    
- **Execution Cost:** High if the language requires many run-time checks (like Java array bounds checking).
    
- **Maintenance Cost:** The highest cost of all. Depends heavily on **Readability**.
    

### 1.4 Influences on Language Design

Two primary factors shape how languages are designed:

#### 1.4.1 Computer Architecture

- **Define:** The underlying hardware structure, specifically the **von Neumann architecture**.
    
- **Explain:** Most computers separate the Memory (data) from the CPU (calculations). Data must be piped back and forth.
    
- **Influence:** This architecture led to **Imperative Languages**.
    
    - **Variables** model memory cells.
        
    - **Assignment statements** model the piping of data.
        
    - **Iteration (Loops)** is efficient because instructions are stored in adjacent memory cells.
        
- **Example:** The concept of `x` = x + 1 is a direct reflection of: "Fetch `x` from memory, add 1 in CPU, pipe result back to memory location `x`."
    

#### 1.4.2 Programming Design Methodologies

- **Define:** Shifts in how we structure software projects.
    
- **Evolution:**
    
    1. **Top-down** design / **Structured programming:** (Late 60s/70s) focused on control structures (getting rid of `GOTO`).
        
    2. **Data-oriented design:** (Late 70s) focused on Abstract Data Types.
        
    3. **Object-oriented design:** (80s) focused on Data Abstraction + Inheritance + Polymorphism (e.g., Smalltalk, Java, C++).
        

### 1.5 Language Categories

1. **Imperative:** Based on variables, assignments, and iteration. (e.g., C, Java, Perl, Visual Basic).
    
2. **Functional:** Based on applying functions to parameters. No variables or assignments in the traditional sense. (e.g., LISP, Scheme, Haskell).
    
3. **Logic:** Rule-based. You state the facts/rules, and the system finds the result. (e.g., Prolog).
    
4. **Object-Oriented:** (Often considered a sub-category of Imperative) Focuses on objects. (e.g., Java, C++).
    

### 1.6 Language Design Trade-Offs

Language design is a balancing act; you cannot have everything.

- **Reliability vs. Cost of Execution:**
    
    - **Example:** Java checks every array index to make sure it is valid (Reliable), but this check takes time (Cost). C does not check (Fast, but Unsafe).
        
- **Readability vs. Writability:**
    
    - **Example:** **APL** has many powerful operators. You can write a complex matrix operation in one line (High Writability), but it looks like alien hieroglyphs to read (Low Readability).
        
- **Writability vs. Reliability:**
    
    - **Example:** C++ pointers allow you to do anything (High Writability/Flexibility), but it is very easy to crash the system (Low Reliability).
        

### 1.7 Implementation Methods

How does the computer actually run the code?

#### 1.7.1 Compilation

- **Define:** Programs are translated completely into machine language (binary) _before_ execution.
    
- **Process:**
    
    1. **Lexical Analysis:** Converts characters into "words" (tokens).
        
    2. **Syntax Analysis:** Builds a structure (parse tree).
        
    3. **Code Generation:** Creates machine code.
        
- **Pros/Cons:** Very fast execution, but slow translation step.
    
- **Example:** C, C++, COBOL.
    

#### 1.7.2 Pure Interpretation

- **Define:** Programs are interpreted by another program (interpreter) line-by-line. No translation to machine code occurs.
    
- **Pros/Cons:** Easy to debug (errors point right to the line), but very slow execution (10-100x slower) because every statement is decoded every time it runs.
    
- **Example:** Early LISP, classic BASIC, some Web scripting.
    

#### 1.7.3 Hybrid Implementation Systems

- **Define:** A compromise. Translates high-level language to an **Intermediate Code** (Bytecode), which is then interpreted.
    
- **Explain:** Faster than pure interpretation, slower than compilation. Provides portability (the intermediate code can run on any machine with a virtual machine).
    
- **Example:** **Java** (translates to Bytecode, run by JVM), **Perl**.
    

#### 1.7.4 Preprocessors

- **Define:** A tool that processes the code _just before_ compilation.
    
- **Explain:** It acts as a "Macro Expander," copying files or replacing text strings.
    
- **Example:** In C, `#include "myLib.h"` tells the preprocessor to copy the code from `myLib.h` right there.
    

### 1.8 Programming Environments

A programming environment is the collection of tools used in software development.

- **Simple Environments:** A file system, a text editor, and a compiler (Command line).
    
- **UNIX:** An operating system that acts as a powerful programming environment with many individual tools (pipe, grep, make).
    
- **Integrated Development Environments (IDEs):** Complex graphical systems that combine the editor, compiler, debugger, and file manager into one uniform interface.
    
    - **Examples:** Microsoft Visual Studio, NetBeans, Borland JBuilder.
        

### End Matter

#### Summary

Studying language concepts improves your ability to express ideas, choose languages, learn new ones, and understand implementation. We evaluate languages based on Readability, Writability, Reliability, and Cost. These are influenced by Computer Architecture (von Neumann) and Design Methodologies.

#### Review Questions (Self-Test)

1. **Why study language concepts?** To express complex ideas and learn new languages faster.
    
2. **Dominant Scientific Language?** Fortran.
    
3. **Dominant Business Language?** COBOL.
    
4. **Dominant AI Language?** LISP.
    
5. **Most UNIX is written in?** C.
    
6. **Disadvantage of too many features?** Reduced readability (feature multiplicity).
    
7. **What is Orthogonality?** The ability to combine primitives freely without exceptions.
    
8. **Compilation vs. Interpretation?** Compilation translates once (fast run); Interpretation decodes every time (slow run).
    
9. **What is a Hybrid System?** Uses intermediate code (like Java Bytecode).
    
10. **What is an IDE?** Integrated Development Environment (like Visual Studio).