# Chapter 1: Preliminaries

## 1.1 Reasons for Studying Concepts of Programming Languages

Understanding the fundamental concepts of programming languages is essential for computer scientists, extending beyond the mere ability to write code in a specific language.

### 1. Increased capacity to express ideas

The depth of human thought is influenced by the expressive power of the language used. In programming, the language limits the control structures, data structures, and abstractions a developer can utilize.

- **Context:** By learning new constructs, programmers expand their mental toolkit. Even if a specific language lacks a feature, a programmer who understands the _concept_ can often simulate it.
    
- **[Real World Example]:** A C programmer familiar with **Associative Arrays (Hashes)** in Perl might design a struct system to simulate that functionality in C.
    
    **Perl (Native Feature):**
    
    ```
    # Simple, expressive creation of an associative array
    my %capitals = ("France" => "Paris", "Spain" => "Madrid");
    print $capitals{"France"};
    ```
    
    **C (Simulation required):**
    
    A C programmer ignorant of this concept might struggle, but one who knows it can simulate it:
    
    ```
    struct KeyValue {
        char* key;
        char* value;
    };
    // Requires manual array management and search algorithms
    struct KeyValue capitals[] = { {"France", "Paris"}, {"Spain", "Madrid"} };
    ```
    

### 2. Improved background for choosing appropriate languages

Many programmers rely on languages they already know, regardless of fit. A broad knowledge base allows for informed selection based on feature suitability rather than familiarity.

### 3. Increased ability to learn new languages

The field is in continuous evolution. Understanding fundamental concepts (grammar, memory models, OO) makes learning a second language significantly easier.

- **Analogy:** Moving from C++ to Java is easier if you understand the underlying concept of **Object-Oriented Programming** (Classes, Inheritance, Polymorphism).
    
- **TIOBE Index:** Acknowledged as an indicator of language popularity, showing that language dominance is dynamic.
    

### 4. Better understanding of the significance of implementation

Understanding _how_ a language is implemented (compiler vs. interpreter, memory management) allows programmers to write efficient code and debug effectively.

- **Example:** If a developer knows that a loop uses strict **Stack** memory allocation while recursion might overhead the stack frame, they can choose the right approach for limited-memory systems.
    

### 5. Better use of languages that are already known

Languages are often complex. Studying concepts reveals obscure features (e.g., C++ templates or Python decorators) within languages the programmer is already using but not fully exploiting.

## 1.2 Programming Domains

Different application domains require languages with specific capabilities.

### 1.2.1 Scientific Applications

Characterized by simple data structures (arrays, matrices) but requiring large numbers of floating-point arithmetic computations.

- **Key Language:** **Fortran** (Formula Translating System).
    
- **Why:** Efficiency was the primary concern.
    
    ```
    ! Fortran handles array math natively and efficiently
    C = MATMUL(A, B)
    ```
    

### 1.2.2 Business Applications

Characterized by the need to produce elaborate reports, store decimal numbers precisely, and manipulate character data.

- **Key Language:** **COBOL**.
    
- **Why:** Strong support for decimal arithmetic (avoiding floating-point rounding errors common in C/Java).
    

### 1.2.3 Artificial Intelligence (AI)

Characterized by **Symbolic Computation** (manipulating names/symbols rather than numbers) and the use of linked lists.

- **Key Languages:** LISP, Prolog, Scheme.
    

### 1.2.4 Systems Programming

Involves the operating system and support tools. Requirements include execution efficiency and low-level access to hardware.

- **Key Language:** **C** (and C++).
    
- **Why:** It is low-level, efficient, and allows direct memory manipulation.
    

### 1.2.5 Web Software

A collection of languages supporting the World Wide Web.

- **Markup:** HTML.
    
- **Scripting:** JavaScript, PHP.
    
- **General Purpose:** Java.
    

## 1.3 Language Evaluation Criteria

There are four primary criteria for evaluating programming languages: **Readability**, **Writability**, **Reliability**, and **Cost**.

### 1.3.1 Readability

The ease with which programs can be read and understood. This is crucial for **Maintenance**, which dominates the software life cycle.

#### 1.3.1.1 Overall Simplicity

- **Feature Multiplicity:** Having multiple ways to accomplish the same operation reduces readability because a reader might not know all the variations.
    
    **Example (Java Incrementing):**
    
    ```
    count = count + 1;  // Method 1
    count += 1;         // Method 2
    count++;            // Method 3
    ++count;            // Method 4
    ```
    
- **Operator Overloading:** A single operator symbol having multiple meanings.
    
    **Bad Example (C++):**
    
    ```
    // If a programmer defines '+' to subtract for a specific class:
    Vector v3 = v1 + v2; // Confusing! Does this add or subtract?
    ```
    

#### 1.3.1.2 Orthogonality

A relatively small set of primitive constructs can be combined in a relatively small number of ways, and every possible combination is legal.

- **Definition:** The meaning of a feature is independent of the context in which it appears.
    
    **Non-Orthogonal Example (IBM Mainframe Assembly):**
    
    You need different instructions depending on where the data is located.
    
    ```
    A  Reg1, memory_cell   ; 'A' adds memory to register
    AR Reg1, Reg2          ; 'AR' adds register to register
    ; You cannot use 'A' for two registers. This is a lack of orthogonality.
    ```
    
    **Orthogonal Example (VAX Assembly):**
    
    The instruction is the same regardless of operand location.
    
    ```
    ADDL Reg1, memory_cell ; 'ADDL' works here
    ADDL Reg1, Reg2        ; 'ADDL' works here too
    ```
    
    **Context Dependence Example (C Language):**
    
    In C, the meaning of `+` changes based on variable type.
    
    ```
    int *p;
    int x = 1;
    // If p points to a 4-byte integer, this adds 4 bytes to the address.
    // If p pointed to a 1-byte char, it would add 1 byte.
    p = p + x;
    ```
    

#### 1.3.1.3 Data Types

Adequate facilities for defining data types aid readability.

- **Bad (C89 style):** `int timeout = 1;` (Is this a number or a flag?)
    
- **Good (Java/Modern C):** `boolean timeout = true;` (Clearly a flag).
    

#### 1.3.1.4 Syntax Design

- **Special Words:** Using explicit closers like `end if` is often more readable than generic braces.
    
    **Ada (Explicit):**
    
    ```
    if X > 0 then
        X := X + 1;
    end if;  -- Very clear what is ending
    ```
    
    **C/Java (Generic):**
    
    ```
    if (x > 0) {
        x++;
    } // Is this closing the if, a loop, or the function?
    ```
    
- **Form and Meaning:** The appearance of a statement should suggest its purpose. `grep` is a classic example of obscure naming (from `g/re/p`), whereas `Search-String` would have been more readable.
    

### 1.3.2 Writability

A measure of how easily a language can be used to create programs.

#### 1.3.2.1 Simplicity and Orthogonality

A smaller number of primitives with consistent rules allows the programmer to design solutions without fighting the language or remembering complex exceptions.

#### 1.3.2.2 Support for Abstraction

The ability to define and use complex structures/operations while ignoring details.

- **Process Abstraction:** Subprograms (e.g., `sort(list)`).
    
- **Data Abstraction:** Classes or Structs.
    
    **Without Data Abstraction (Fortran 77 style):**
    
    Managing a binary tree using parallel arrays is tedious and error-prone.
    
    ```
    INTEGER LEFT_CHILD(100)
    INTEGER RIGHT_CHILD(100)
    INTEGER DATA(100)
    ```
    
    **With Data Abstraction (Java):**
    
    ```
    class Node {
        Node left;
        Node right;
        int data;
    }
    ```
    

#### 1.3.2.3 Expressivity

The existence of convenient ways to specify computations.

- `count++` is more expressive than `count = count + 1`.
    
- APL is famous for extremely high expressivity (doing matrix math in a single symbol), often at the cost of readability.
    

### 1.3.3 Reliability

A program is reliable if it performs to specifications under all conditions.

#### 1.3.3.1 Type Checking

Testing for type errors.

- **Compile-time checking (Static):** Detects errors before the program runs (e.g., Java).
    
- **Run-time checking (Dynamic):** Detects errors as lines execute (e.g., Python).
    
- **Failure Example (Original C):**
    
    Original C allowed passing an `int` to a function expecting a `float` without warning, causing the bits to be interpreted incorrectly and corrupting data.
    

#### 1.3.3.2 Exception Handling

The ability to intercept run-time errors.

```
// Java: High Reliability via Exception Handling
try {
    readFile();
} catch (IOException e) {
    System.out.println("File missing, using default config.");
}
```

#### 1.3.3.3 Aliasing

Having two or more distinct names that access the same memory cell.

- **Risk:** Changing one variable silently changes the other.
    
    **C++ Example:**
    
    ```
    void confusingFunc(int *a, int *b) {
        *a = 10;
        *b = 20;
        // If a and b point to the same address, *a is now 20, not 10!
    }
    ```
    

### 1.3.4 Cost

The total cost includes:

1. **Training:** How hard is it to learn?
    
2. **Writing:** How long does it take to code?
    
3. **Compiling:** Optimization levels vs. compile speed.
    
4. **Execution:** Does the language run fast? (Java bounds checking adds safety but costs time).
    
5. **Reliability:** Cost of failure (e.g., in a nuclear plant).
    
6. **Maintenance:** The highest cost in the lifecycle.
    

## 1.4 Influences on Language Design

### 1.4.1 Computer Architecture

Most popular languages (Imperative) are designed around the **von Neumann architecture**.

- **Von Neumann Bottleneck:** The speed limit imposed by the connection between the CPU and Memory.
    
- **Fetch-Execute Cycle:**
    
    1. Fetch instruction.
        
    2. Increment counter.
        
    3. Decode instruction.
        
    4. Execute instruction.
        

### 1.4.2 Programming Design Methodologies

- **1960s/70s:** Structured Programming (Top-down design).
    
- **Late 1970s:** Data-Oriented Design (Abstract Data Types).
    
- **1980s - Present:** Object-Oriented Design (Inheritance, Polymorphism).
    

## 1.5 Language Categories

1. **Imperative:** Variables, assignment, iteration. (C, Java, Perl).
    
2. **Functional:** Applying functions to parameters. No assignment state. (LISP, Scheme, Haskell).
    
3. **Logic:** Rule-based. (Prolog).
    
4. **Visual:** Drag-and-drop code. (.NET).
    

## 1.6 Language Design Trade-Offs

- **Reliability vs. Cost of Execution:**
    
    - **Java:** Enforces array index checking. (Safe, but slower).
        
    - **C:** No index checking. (Fast, but risk of buffer overflow).
        
- **Writability vs. Readability:**
    
    - **APL:** `(+ / A) ÷ ρ A` (Calculates average). Very writable (concise), very hard to read.
        

## 1.7 Implementation Methods

### 1.7.1 Compilation

Translates source code completely into machine language before execution.

- **Flow:** Source -> Lexical Analysis -> Syntax Analysis -> Semantic Analysis -> Code Gen -> Machine Code.
    
- **Pros:** Fast execution.
    

### 1.7.2 Pure Interpretation

A software program simulates a machine and executes source code line-by-line.

- **Pros:** Excellent debugging (errors point to source lines).
    
- **Cons:** Slow (10-100x slower than compiled).
    
- **Examples:** Early BASIC, JavaScript (historically).
    

### 1.7.3 Hybrid Implementation Systems

Compiles to an intermediate language (Byte Code), which is then interpreted.

- **Example:** **Java**.
    
    - Source (`.java`) -> Compiler -> Bytecode (`.class`) -> JVM (Interpreter/JIT).
        

### 1.7.4 Preprocessors

Processes code _before_ compilation (Macro expansion).

- **Example (C Macros):**
    
    ```
    #define max(A, B) ((A) > (B) ? (A) : (B))
    ```
    
    - **Side Effect Risk:**
        
        If you call `max(x++, y)`, the variable `x` might be incremented _twice_ because the macro duplicates the expression `A` in the output code.
        

## 1.8 Programming Environments

- **UNIX:** Portable OS with toolsets (grep, pipe).
    
- **Visual Studio .NET:** Large, windowed environment.
    
- **NetBeans:** Integrated environment for Java.