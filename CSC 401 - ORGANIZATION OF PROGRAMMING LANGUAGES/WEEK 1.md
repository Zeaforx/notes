# Chapter 1: Preliminaries

## Course: Concepts of Programming Languages

### Introduction

This chapter establishes the foundation for understanding why we study programming languages, how they are evaluated, the historical and architectural influences on their design, and the methods used to implement them.

## 1.1 Reasons for Studying Concepts of Programming Languages

Students often question why they need to study language concepts if they already know a popular language like Java or C++. There are six primary justifications for this field of study:

1. **Increased capacity to express ideas:**
    
    The language in which we communicate influences the depth and complexity of our thoughts. If a programmer is only familiar with one language, their ability to construct algorithms is limited by the constructs of that specific language.
    
    - _Example:_ Awareness of associative arrays in Perl might lead a C programmer to simulate them, even though C doesn't support them natively.
        
2. **Improved background for choosing appropriate languages:**
    
    Many programmers choose languages based on familiarity rather than suitability. A solid understanding of language concepts allows a developer to select the language that best fits the specific problem domain.
    
3. **Increased ability to learn new languages:**
    
    Computer science is a rapidly evolving field. Understanding the underlying concepts (grammar, types, control structures) makes learning a second or third language significantly easier, just as understanding grammar helps in learning natural languages.
    
4. **Better understanding of the significance of implementation:**
    
    Understanding how language constructs are implemented (e.g., how a computer manages recursion or array indexing) allows programmers to use the language more efficiently and find bugs related to implementation details.
    
5. **Better use of languages that are already known:**
    
    Languages are often complex. By studying general concepts, programmers often discover features within their primary languages that they were previously unaware of or didn't understand how to utilize.
    
6. **Overall advancement of computing:**
    
    If those who select languages for projects are well-informed, better languages will be adopted, and poorer languages will fade away.
    
    - _Historical Context:_ Many believe ALGOL 60 was superior to Fortran in the 1960s, but lack of understanding prevented its widespread adoption.
        

> **The Professor's Insight:**
> 
> Think of this like a carpenter studying different types of wood and joinery. Even if you mostly build pine cabinets, knowing the properties of oak or the mechanics of a dovetail joint makes you a master builder, not just a laborer. It prevents "Maslow's Hammer"—where if the only tool you have is a hammer, everything looks like a nail.

## 1.2 Programming Domains

Different application areas require different language features.

### 1.2.1 Scientific Applications

- **Characteristics:** Large numbers of floating-point arithmetic computations; relatively simple data structures (arrays/matrices).
    
- **Key Languages:** Fortran (the first), ALGOL 60.
    
- **Status:** Efficiency is key; Fortran is still widely used.
    

### 1.2.2 Business Applications

- **Characteristics:** Capabilities for producing elaborate reports; precise decimal numbers (currency); character data storage.
    
- **Key Language:** COBOL (appeared in 1960).
    
- **Status:** COBOL is still the dominant language for legacy business systems.
    

### 1.2.3 Artificial Intelligence (AI)

- **Characteristics:** Symbolic computation (manipulating names/symbols rather than numbers); use of linked lists; flexibility (code execution during runtime).
    
- **Key Languages:** LISP (Functional), Prolog (Logic).
    
- **Status:** Early AI used LISP/Prolog; modern AI often uses Python or C, though the concepts remain.
    

### 1.2.4 Systems Programming

- **Characteristics:** Operating systems and support tools; requires execution efficiency and low-level hardware access.
    
- **Key Languages:** PL/S, BLISS, C, C++.
    
- **Status:** The UNIX OS is written almost entirely in C.
    

### 1.2.5 Web Software

- **Characteristics:** Dynamic content; eclectic collection of languages.
    
- **Key Languages:** HTML (Markup), Java (General Purpose), JavaScript/PHP (Scripting).
    

|   |   |   |
|---|---|---|
|**Domain**|**Primary Focus**|**Representative Languages**|
|**Scientific**|Floating-point math, Arrays|Fortran, ALGOL|
|**Business**|Reporting, Decimal Arithmetic|COBOL|
|**AI**|Symbolic manipulation, Linked Lists|LISP, Prolog, Scheme|
|**Systems**|Efficiency, Hardware Access|C, C++, BLISS|
|**Web**|Markup, Dynamic Content|HTML, JavaScript, PHP|

## 1.3 Language Evaluation Criteria

This is the framework used to judge the quality of a language.

### 1.3.1 Readability

The ease with which programs can be read and understood. This is crucial for maintenance.

#### 1.3.1.1 Overall Simplicity

- **Manageable Set of Features:** A language with too many features leads to programmers learning only a subset.
    
- **Feature Multiplicity:** Having more than one way to accomplish the same operation.
    
    - _Example in Java:_ Incrementing an integer:
        
          
        
        $$count = count + 1$$$$count += 1$$$$count++$$$$++count$$
- **Operator Overloading:** A single operator symbol having more than one meaning. While useful (e.g., `+` for integer and float addition), it harms readability if users can define their own confusing overloadings (e.g., using `+` to subtract).
    

#### 1.3.1.2 Orthogonality

**Definition:** **Orthogonality** means that a relatively small set of primitive constructs can be combined in a relatively small number of ways, and every possible combination is legal and meaningful.

- **Low Orthogonality Example (IBM Mainframe):** Adding two integers required different instructions depending on whether the operands were in registers or memory (`A` vs `AR`).
    
- **High Orthogonality Example (VAX):** A single `ADDL` instruction could accept operands from either registers or memory in any combination.
    
- _Note:_ Too much orthogonality (ALGOL 68) can lead to unnecessary complexity where any structure can be placed anywhere.
    

#### 1.3.1.3 Data Types

Adequate facilities for defining data types aid readability.

- _Example:_ Using a specific `Boolean` type for a flag (`timeout = true`) is more readable than using a numeric type (`timeout = 1`).
    

#### 1.3.1.4 Syntax Design

- **Special Words:** Using `end if` and `end loop` (Ada) is more readable than generic `}` closers (C/Java).
    
- **Form and Meaning:** Syntactic form should suggest meaning. The UNIX command `grep` is a poor design example because the word implies nothing about its search function.
    

### 1.3.2 Writability

The measure of how easily a language can be used to create programs.

#### 1.3.2.1 Simplicity and Orthogonality

A programmer should be able to design a solution using a small set of primitives. Too many primitives or a lack of orthogonality makes writing difficult because the programmer must remember many exceptions to rules.

#### 1.3.2.2 Support for Abstraction

**Definition:** **Abstraction** is the ability to define and use complicated structures or operations in ways that allow many of the details to be ignored.

- **Process Abstraction:** Using a subprogram (e.g., a `sort()` function) so the sorting logic doesn't need to be replicated.
    
- **Data Abstraction:** Using a `BinaryTree` class is easier than managing three parallel integer arrays (Fortran 77 style) to simulate a tree.
    

#### 1.3.2.3 Expressivity

The presence of convenient ways to specify computations.

- _Example:_ `count++` is more expressive than `count = count + 1`.
    
- _Example:_ `for` loops are more convenient than `while` loops for counting.
    

### 1.3.3 Reliability

A program is reliable if it performs to its specifications under all conditions.

#### 1.3.3.1 Type Checking

Testing for type errors.

- **Compile-time checking** is preferred over **run-time checking** because it is cheaper and catches errors earlier.
    
- _Failure Example:_ Original C did not check parameter types, leading to crashes if an `int` was passed to a function expecting a `float`.
    

#### 1.3.3.2 Exception Handling

**Definition:** **Exception Handling** is the ability of a program to intercept run-time errors (or other unusual conditions), take corrective measures, and continue execution.

- Supported in C++, Java, C#, Ada; absent in original C and Fortran.
    

#### 1.3.3.3 Aliasing

**Definition:** **Aliasing** occurs when two or more distinct names can be used to access the same memory cell.

- This is generally dangerous for reliability because changing the value via one name implicitly changes it for the other, often without the programmer realizing.
    

#### 1.3.3.4 Readability and Writability

If a language is difficult to read or write, the likelihood of introducing bugs increases naturally.

### 1.3.4 Cost

The total cost includes:

1. **Training:** Function of simplicity.
    
2. **Writing Programs:** Function of writability.
    
3. **Compiling:** Cost of the tool and time.
    
4. **Execution:** Run-time type checks increase safety but decrease speed.
    
5. **Language Implementation System:** Availability of free/cheap compilers (e.g., Java's success).
    
6. **Reliability:** Cost of failure (e.g., nuclear plant, X-ray machine).
    
7. **Maintenance:** The cost of corrections and modifications.
    

> **The Professor's Insight:**
> 
> For large, long-lived systems, **Maintenance** is the most significant cost factor (up to 2-4x development cost). Therefore, **Readability** is arguably the most important criterion for professional software development, even more so than Writability.

## 1.4 Influences on Language Design

### 1.4.1 Computer Architecture

Most languages are designed around the **Von Neumann Architecture**.

**Definition:** **Von Neumann Architecture** is a computer design where data and programs are stored in the same memory. The CPU is separate from memory, and instructions/data must be piped between them.

- **Imperative Languages:** Variables model memory cells; assignment statements model the piping of data; iteration models the efficient execution of adjacent instructions.
    
- **Fetch-Execute Cycle:**
    
    1. Initialize program counter.
        
    2. Fetch instruction.
        
    3. Increment counter.
        
    4. Decode instruction.
        
    5. Execute instruction.
        
- **Von Neumann Bottleneck:** The speed of the connection between memory and the processor is the primary limiting factor in computer speed.
    

**[Visual Note: Figure 1.1 in text]**

_The diagram depicts the CPU (containing the Control Unit and Arithmetic Logic Unit) separated from Memory. A bus (channel) connects them, moving instructions and data back and forth._

### 1.4.2 Programming Design Methodologies

- **1960s-1970s:** Structured programming (Top-down design, Stepwise refinement). Shifted focus from `goto` statements to control structures (`while`, `if`).
    
- **Late 1970s:** Data-oriented design. Focus on Abstract Data Types (SIMULA 67).
    
- **1980s-Present:** Object-Oriented Design. Data abstraction + Inheritance + Dynamic method binding (Smalltalk, Java, C++).
    

## 1.5 Language Categories

1. **Imperative:** Based on Von Neumann architecture (variables, assignments, iteration). Examples: C, Java, Perl.
    
2. **Functional:** Based on mathematical functions. Computations are applying functions to parameters. Examples: LISP, Scheme, F#.
    
3. **Logic:** Rule-based. Rules are specified in no particular order. Example: Prolog.
    
4. **Object-Oriented:** (Not strictly a separate category, but an extension of imperative). Support for objects, classes, inheritance.
    
5. **Visual:** Drag-and-drop generation of code (e.g., .NET languages in Visual Studio).
    
6. **Markup/Hybrid:** HTML/XML (not programming languages) extended with JSTL or XSLT.
    

## 1.6 Language Design Trade-Offs

Language design is an engineering task requiring reconciliation of conflicting criteria.

- **Reliability vs. Cost of Execution:**
    
    - _Example:_ Java checks all array indices. This ensures reliability but makes execution slower. C does not check, making it faster but less reliable.
        
- **Readability vs. Writability:**
    
    - _Example:_ APL has powerful operators allowing complex calculations in one line (high Writability) but is incredibly difficult to decipher (low Readability).
        
- **Writability vs. Reliability:**
    
    - _Example:_ C++ pointers are flexible (high Writability) but dangerous (low Reliability). Java eliminated pointers for this reason.
        

## 1.7 Implementation Methods

### 1.7.1 Compilation

Programs are translated into machine language, which is then executed directly on the computer.

- **Advantage:** Very fast program execution.
    
- **Process:** Source Program $\rightarrow$ Lexical Analysis $\rightarrow$ Syntax Analysis (Parse Trees) $\rightarrow$ Intermediate Code $\rightarrow$ Code Generator $\rightarrow$ Machine Language.
    
- **Linking:** Connecting the user program to system programs (OS).
    

**[Visual Note: Figure 1.3 in text]**

_Shows the pipeline: Lexical Analyzer gathers characters into units_ $\rightarrow$ _Syntax Analyzer builds parse trees_ $\rightarrow$ _Semantic Analyzer checks types_ $\rightarrow$ _Code Generator makes machine code._

### 1.7.2 Pure Interpretation

Programs are interpreted by another program (the interpreter) with no translation. Software simulates a machine.

- **Advantage:** Great for debugging (errors refer to source code).
    
- **Disadvantage:** Very slow execution (10-100x slower) because statements are decoded every time they are executed.
    
- **Examples:** Early LISP, modern JavaScript/PHP (in some contexts).
    

### 1.7.3 Hybrid Implementation Systems

A compromise. High-level language is translated to an intermediate language (byte code) that is easily interpreted.

- **Example:** Java. Java is compiled to Byte Code, which is then run on the Java Virtual Machine (JVM).
    
- **Just-in-Time (JIT):** Translates intermediate code to machine code _during_ execution to speed up frequently used methods.
    

### 1.7.4 Preprocessors

A program that processes code immediately before compilation. It is essentially a macro expander.

- _Example:_ C `#include` copies a file into the program. `#define` creates macros.
    

|   |   |   |   |
|---|---|---|---|
|**Method**|**Speed (Execution)**|**Speed (Development)**|**Primary Use**|
|**Compilation**|Fast|Slow (compile steps)|Systems (C/C++)|
|**Interpretation**|Slow|Fast (immediate run)|Scripting (JS/PHP)|
|**Hybrid**|Medium|Medium|Java, .NET|

## 1.8 Programming Environments

A programming environment is the collection of tools used in software development.

- **UNIX:** An older environment with a file system, editor, linker, and compiler. Historically lacked a uniform interface (GUI).
    
- **Borland JBuilder:** Integrated environment for Java.
    
- **Microsoft Visual Studio .NET:** Elaborate, windowed interface for .NET languages.
    
- **NetBeans:** Development environment/framework primarily for Java.