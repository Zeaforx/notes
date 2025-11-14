# Chapter 2: Evolution of the Major Programming Languages

## Introduction: Why Study Language Evolution?

Understanding the history of programming languages is not just a trivia exercise. It helps us understand _why_ modern languages like Python, Java, and C++ are designed the way they are. We can see how ideas were developed, combined, and improved over time. This evolution is driven by two main forces:

1. **Hardware:** Changes in computer hardware (e.g., from no floating-point units to having them, from small memory to vast memory) directly influenced language design.
    
2. **Abstraction:** A constant drive to move "further away" from the raw machine code. We started by managing individual memory bits and now work with high-level concepts like objects, data streams, and logic rules.
    

## 1. Zuse's Plankalkül (1945)

- **Designer:** Konrad Zuse, a German engineer working in isolation during WWII.
    
- **Historical Context:** Designed in 1945 but not published until 1972 due to the post-war chaos. It was **never implemented** in Zuse's time.
    
- **Significance:** It was the first high-level programming language design. It was incredibly advanced for its time, introducing features that wouldn't be seen again for decades.
    
- **Advanced Features:**
    
    - **Data Structures:** Included floating-point numbers, arrays, and records (hierarchical data structures).
        
    - **Invariants:** This was a revolutionary concept. An invariant is a condition or assertion about the program's state that is always true. This is a core idea in modern high-level software design and verification.
        
- **Syntax Example:** The slide shows an assignment statement: `A[5] = A[4] + 1`.
    
    ```
    |   A + 1 => A
    V   |   4              5               (subscripts)
    S   |   1.n           1.n             (data types)
    ```
    
    This notation, while unfamiliar, clearly shows the operation, the array (`A`), the indices (4 and 5), and the data types.
    

## 2. Minimal Hardware Programming: Pseudocodes (Late 1940s - 1950s)

Before compilers, programmers wrote in **machine code** (raw binary numbers). This was:

- **Not Readable:** Just strings of 1s and 0s.
    
- **Not Modifiable:** A tiny change required recalculating all memory addresses.
    
- **Tedious:** No support for common math (like `(A+B)*C`).
    
- **Machine-Dependent:** Code for one computer model was useless on another.
    

**Pseudocodes** were the first step toward solving this. They were not full languages, but ways to make programming easier.

- **Short Code (1949):** Developed for the UNIVAC. It was an _interpreter_, not a compiler. It read expressions (like `X0 = Y0 + Z0`) and executed them one by one. This was slow, but vastly better than machine code.
    
- **Speedcoding (1954):** Developed by John Backus for the IBM 701. The 701 lacked floating-point hardware, so Speedcoding provided software-based floating-point operations. It also included array-handling features. It was also an interpreter and ran very slowly, but it added crucial functionality.
    
- **UNIVAC "Compiling" System (1950s):** Developed by a team led by **Grace Hopper**. This system expanded pseudocode statements into their machine code equivalents. This was a key step toward a true compiler.
    
- **David J. Wheeler (Cambridge):** Developed a method for using "relocatable addresses," which allowed subprogram code to be loaded into any part of memory, a crucial innovation for building larger programs.
    

## 3. IBM 704 and Fortran (1957)

**Fortran (FORmula TRANslating System)** is arguably the first major high-level, compiled language.

- **The Context:** The new **IBM 704** was a game-changer. It had two critical hardware features: **index registers** (for fast array processing) and **floating-point hardware**.
    
- **The "Compiler" Idea:** Because the hardware could now do floating-point math directly, a slow interpreter (like Speedcoding) was unacceptable. John Backus and his team at IBM realized they needed a _translator_ that would take high-level formulas and generate machine code that was _just as fast_ as a human expert's. This was the birth of the **optimizing compiler**.
    
- **Design Goals:**
    
    - **Machine efficiency was the #1 concern.** The code had to be fast.
        
    - Aimed at scientific and engineering applications.
        
    - **No need for:** Dynamic storage (all memory was allocated at the start), string handling, or decimal arithmetic (which is for business).
        

### Evolution of Fortran:

- **Fortran I (1957):**
    
    - Names up to 6 characters.
        
    - `DO` loop (post-test, meaning it always ran at least once).
        
    - Formatted I/O (for reading data cards and printing results).
        
    - User-defined subprograms.
        
    - Arithmetic `IF` statement (a three-way branch: `IF (expr) 10, 20, 30` meant goto 10 if negative, 20 if zero, 30 if positive).
        
    - _Reliability was poor:_ Programs over 400 lines often failed to compile due to the 704's unreliability.
        
- **Fortran II (1958):** Fixed many bugs and, most importantly, introduced **independent compilation**. This allowed a large program to be broken into pieces, with each piece compiled separately and then linked together.
    
- **Fortran IV (1960-62):** Became the standard.
    
    - Added explicit type declarations (e.g., `INTEGER X`).
        
    - Added a logical `IF` statement (e.g., `IF (X .GT. 3) ...`).
        
    - Allowed subprogram names to be passed as parameters.
        
- **Fortran 77 (1978):** A major update that became the standard for decades.
    
    - **Character string handling.**
        
    - Logical loop control (`WHILE`-like).
        
    - **`IF-THEN-ELSE` statement.**
        
- **Fortran 90 (1990):** A massive modernization.
    
    - **Modules:** For building abstract data types.
        
    - **Dynamic Arrays:** Arrays that could change size.
        
    - **Pointers.**
        
    - **Recursion:** Subprograms could call themselves.
        
    - `CASE` statement (a `switch` statement).
        
- **Evaluation:** Fortran _completely changed_ how computers were used. It proved that a high-level language could generate code as fast as an expert assembly programmer. It dominated scientific and engineering computing for over 50 years.
    

## 4. Functional Programming: LISP (1959)

**LISP (LISt Processing)** was created for a completely different problem: Artificial Intelligence (AI).

- **Designer:** John McCarthy at MIT.
    
- **The Context:** AI research didn't need fast number-crunching. It needed to process _symbols_ and _concepts_.
    
- **Design Goals:**
    
    - **Symbolic Computation:** Manipulating symbols (like `CAT` or `DOG`) as easily as numbers.
        
    - **List Processing:** The main data structure is the list, which can hold other lists, allowing for complex, nested data (e.g., `(A (B C) D (E (F G)))`).
        
- **Core Concepts:**
    
    - **Data Types:** Only two: **atoms** (symbols or numbers) and **lists**.
        
    - **Functional Programming:** LISP pioneered this paradigm. It's based on **lambda calculus**. This means:
        
        - Computation is done by evaluating functions.
            
        - There is no need for variables or assignment statements (in pure LISP).
            
        - Control is managed by **recursion** and conditional expressions (not loops).
            
- **LISP Dialects:**
    
    - **Scheme (mid-1970s):** A small, minimalist dialect of LISP from MIT. It emphasized static scoping and treating functions as "first-class entities" (you can pass a function as an argument to another function). It's widely used in computer science education.
        
    - **COMMON LISP (1980s):** An industrial-strength effort to combine the features of many LISP dialects into one large, powerful language.
        

## 5. The First Step Toward Sophistication: ALGOL (1958-1960)

**ALGOL (ALGOrithmic Language)** was the first major language designed by an international committee (ACM in the U.S. and GAMM in Europe).

- **The Context:** Fortran was an IBM-only, _de facto_ standard. There was no universal, machine-independent language for publishing algorithms.
    
- **Design Goals:**
    
    - Be close to standard mathematical notation.
        
    - Be good for describing algorithms.
        
    - Be translatable to machine code.
        

### ALGOL 58 & 60:

- **ALGOL 58:** The initial design. It was more of a proposal and not widely implemented.
    
- **ALGOL 60:** The critical, revised version. It introduced fundamental concepts that are now in almost _every_ modern language:
    
    - **Block Structure:** Using `begin` and `end` to group statements. This introduced the idea of **local scope** (variables declared inside a block only exist within that block).
        
    - **Parameter Passing:** Formalized two methods (pass-by-value and pass-by-name).
        
    - **Recursion:** Allowed subprograms to call themselves (which Fortran did not).
        
    - **Stack-Dynamic Arrays:** Arrays whose size could be determined at runtime when a block was entered.
        

### ALGOL 60 Evaluation: A "Successful Failure"

- **Successes:**
    
    - Became the standard for publishing algorithms for over 20 years.
        
    - **All subsequent imperative languages** (Pascal, C, Ada, Java) are its intellectual descendants.
        
    - It was the first language with a **formal syntax definition (BNF - Backus-Naur Form)**, a major step forward for computer science.
        
- **Failures:**
    
    - **Never widely used** in the U.S.
        
    - **Reasons:** Lack of I/O and string handling (these were left to implementers, so every version was different and non-portable), too flexible (hard to compile), and a lack of support from IBM, which stuck with Fortran.
        

## 6. Computerizing Business Records: COBOL (1960)

**COBOL (COmmon Business-Oriented Language)** was designed to solve a different problem: business data processing.

- **The Context:** Based on **Grace Hopper's** earlier FLOW-MATIC language. The U.S. Department of Defense (DoD) was a key sponsor, wanting a standard language for its business applications.
    
- **Design Goals:**
    
    - **Look like simple English.** The goal was for managers to be able to read it (e.g., `ADD TAX TO TOTAL GIVING GRAND-TOTAL`).
        
    - **Be easy to use,** even if less powerful.
        
    - Must not be biased by compiler problems.
        
- **Key Contributions:**
    
    - **Separate Data Division:** This was a major innovation. It forced programmers to define all data structures (called **records**) in one place, separate from the program's logic. This made programs much easier to maintain.
        
    - **Hierarchical Data Structures:** Natively supported records-within-records (e.g., a `CUSTOMER-RECORD` containing an `ADDRESS` field, which itself contained `STREET`, `CITY`, and `ZIP`).
        
    - Long names (up to 30 characters) with hyphens.
        
- **Evaluation:** The DoD's influence (requiring it for contracts) made COBOL a massive success. It became (and in many ways, still is) the most widely used language for business applications on mainframe computers.
    

## 7. The Beginning of Timesharing: BASIC (1964)

**BASIC (Beginner's All-purpose Symbolic Instruction Code)** was developed at Dartmouth College by Kemeny and Kurtz.

- **The Context:** Its design was tied to the rise of **timesharing** systems, where many users could interact with a single computer at the same time using terminals.
    
- **Design Goals:**
    
    - Be extremely simple for non-computer-science students to learn.
        
    - Be **interactive**. Unlike "batch" languages (Fortran, COBOL) where you submitted a job and waited, BASIC was a "conversational" language where you could type a command and get an instant response.
        
- **Evaluation:** BASIC's simplicity and interactive nature made it the standard language for the first generation of microcomputers (Apple II, Commodore 64) and the gateway to programming for millions of people.
    

## 8. Everything for Everybody: PL/I (1964)

By the mid-60s, the computing world was split:

- **Scientific Users:** Used Fortran. Needed better I/O.
    
- **Business Users:** Used COBOL. Needed floating-point math for new "Management Information Systems" (MIS).
    

**PL/I (Programming Language One)** was IBM's attempt to create one language to "rule them all."

- **Design:** Developed by IBM and its SHARE user group. It was essentially a combination of all the features of Fortran, COBOL, and ALGOL 60.
    
- **Contributions (New Features):**
    
    - **Concurrency:** The first language with built-in support for "unit-level concurrency" (running tasks in parallel).
        
    - **Exception Handling:** A formal `ON` condition system to catch and handle errors.
        
    - **Pointers:** The first pointer data type in a major language.
        
    - **Array Cross-Sections:** A powerful way to refer to slices of multi-dimensional arrays.
        
- **Evaluation:** PL/I was a commercial success for IBM users but was not widely adopted outside of that ecosystem. Its legacy is that it was **too large and complex**. It was the first "kitchen sink" language, and many of its features were considered poorly designed.
    

## 9. Early Dynamic Languages: APL and SNOBOL

These languages were characterized by **dynamic typing** (a variable's type is set when a value is assigned, not by a declaration) and **dynamic storage allocation**.

- **APL (A Programming Language, c. 1960):**
    
    - Designed by Ken Iverson as a hardware description language.
        
    - It is **highly expressive** and uses a unique, symbolic (often Greek) character set. A single character could trigger a complex matrix operation.
        
    - This made programs very short but also famously difficult to read (often called a "write-only" language).
        
- **SNOBOL (1964):**
    
    - Designed at Bell Labs for **string manipulation**.
        
    - Its key feature was powerful, built-in operators for **string pattern matching**.
        
    - It was slow, but its pattern-matching abilities were a major influence on later text-processing tools (like `grep` and Perl).
        

## 10. The Beginning of Data Abstraction: SIMULA 67 (1967)

SIMULA 67 is one of the most intellectually important languages ever created.

- **Designers:** Nygaard and Dahl in Norway.
    
- **The Context:** It was designed for **system simulation** (e.g., simulating traffic, ecological systems, etc.).
    
- **The Problem:** Modeling real-world systems was difficult. The designers realized they needed to model real-world "objects" that had their own properties and behaviors.
    
- **Key Contributions (The Birth of OOP):**
    
    - **Classes:** The "blueprint" for an object (e.g., a `Car` class).
        
    - **Objects:** An instance of a class (e.g., `myRedCar`).
        
    - **Inheritance:** A mechanism for a new class (`Truck`) to be a specialized version of an existing class (`Vehicle`).
        
    - **Coroutines:** A type of subprogram that can be paused and resumed, allowing multiple tasks to be simulated in parallel.
        

SIMULA 67 was not a commercial success, but its ideas directly inspired Smalltalk and C++.

## 11. Orthogonal Design: ALGOL 68 (1968)

This was a separate effort to create a successor to ALGOL 60.

- **Key Concept: Orthogonality.** This is a design principle where a small set of basic concepts can be combined in any way without special restrictions.
    
    - _Example:_ If a language has "integers" and "arrays," an orthogonal design lets you have "arrays of integers." If it adds "user-defined types," you can _also_ have "arrays of user-defined types" and "user-defined types that contain arrays."
        
- **Contributions:**
    
    - **User-defined data structures (structs).**
        
    - **Reference types** (a safer form of pointers).
        
- **Evaluation:** ALGOL 68 was even _less_ successful than ALGOL 60. It was seen as overly complex and difficult to implement. However, its "orthogonal" ideas and specific features strongly influenced Pascal, C, and Ada.
    

## 12. Pascal (1971)

- **Designer:** Niklaus Wirth (who was on the ALGOL 68 committee and disliked its complexity).
    
- **Design Goal:** To create a small, simple language for teaching **structured programming**.
    
- **Structured Programming:** This is the philosophy of avoiding `GOTO` statements and using clean control structures like `if-then-else`, `while` loops, and `for` loops.
    
- **Evaluation:** Pascal was a massive success in education. From the mid-70s to the late-90s, it was the primary language used to teach programming, instilling good habits in a generation of developers.
    

## 13. C (1972)

- **Designer:** Dennis Ritchie at Bell Labs.
    
- **The Context:** Developed alongside the **UNIX** operating system. C was created to be the language to _write_ UNIX in.
    
- **Design Goal:** To be a **systems programming language** (for writing operating systems, compilers, and device drivers). It evolved from earlier, typeless languages (BCLP and B).
    
- **Core Philosophy:** It's often called a "high-level assembler." It provides high-level structures (loops, `if`, functions) but also low-level access to machine memory via **pointers**.
    
- **Features:**
    
    - Powerful set of operators.
        
    - **Weak type checking:** This gives the programmer power but is also a major source of bugs (e.g., buffer overflows).
        
- **Evaluation:** C became one of the most influential and widely used languages in history, forming the backbone of UNIX, Linux, Windows, and countless applications that require high performance.
    

## 14. Programming Based on Logic: Prolog (1972)

**Prolog (Programming in Logic)** represented a completely different paradigm.

- **The Paradigm: Logic Programming.**
    
    - **Imperative Languages (C, Pascal):** You tell the computer _how_ to solve a problem (step-by-step instructions).
        
    - **Logic Languages (Prolog):** You tell the computer _what is true_ (a set of **facts** and **rules**). You then _ask the computer a query_, and its "inferencing engine" uses the facts and rules to find the answer.
        
- **Example:**
    
    - **Fact:** `parent(john, bill).`
        
    - **Rule:** `grandparent(X, Y) :- parent(X, Z), parent(Z, Y).`
        
    - **Query:** `grandparent(john, Who).`
        
    - **Result:** `Who = bill` (Oops, that's wrong. The result would be based on finding a `Z` that links `john` and `Y`). _Correction based on logic:_ If we add `parent(bill, sue)`, the query `grandparent(john, Who)` would result in `Who = sue`.
        
- **Evaluation:** Prolog is not used for general-purpose programming due to inefficiency, but it is a cornerstone of AI research, expert systems, and computational linguistics.
    

## 15. History's Largest Design Effort: Ada (1979)

- **The Context:** The U.S. DoD was spending billions on software for **embedded systems** (missiles, aircraft, tanks). This software was written in hundreds of different, unsafe languages.
    
- **The Goal:** Create _one_ safe, reliable, and maintainable language for all DoD projects. The design was chosen from a massive competition.
    
- **Key Contributions (Features for Reliability):**
    
    - **Packages:** A powerful module system for supporting data abstraction and encapsulation.
        
    - **Exception Handling:** A robust system for handling runtime errors, critical for fault-tolerant systems.
        
    - **Generic Program Units:** (Similar to C++ templates) for writing reusable code.
        
    - **Concurrency ("Tasking"):** Built-in features for creating and synchronizing parallel tasks, essential for real-time systems.
        
- **Evaluation:**
    
    - **Ada 95:** A major revision that added full Object-Oriented Programming (OOP) features.
        
    - Ada is an excellent, safe, and powerful language. However, its popularity suffered when the DoD eventually stopped mandating its use, and it lost ground to the C/C++ ecosystem.
        

## 16. Object-Oriented Programming: Smalltalk (1970s)

- **Designer:** Alan Kay at **Xerox PARC**.
    
- **The Philosophy:** While SIMULA 67 _invented_ objects, Smalltalk established the _pure philosophy_ of OOP.
    
    - **Everything is an object.**
        
    - Objects communicate by **sending messages** to each other.
        
- **Key Contributions:**
    
    - The first _full_ implementation of OOP (data abstraction, inheritance, and **dynamic binding** - deciding at runtime which method to call).
        
    - Smalltalk was developed in an integrated environment that **pioneered the Graphical User Interface (GUI)**. Windows, icons, menus, and the mouse were all developed as part of the Smalltalk system (all were, of course, _objects_).
        

## 17. Combining Imperative and OO: C++ (c. 1983)

- **Designer:** Bjarne Stroustrup at Bell Labs.
    
- **The Goal:** To add the OOP features of SIMULA 67 (classes, inheritance) to the C language. He wanted the organizational power of OOP with the speed and low-level access of C.
    
- **Core Philosophy:** A "hybrid" language. You can write procedural C code, or you can write full OOP code, or (most commonly) mix them.
    
- **Evaluation:** C++ became incredibly popular for high-performance applications (video games, financial trading, scientific simulation). It is extremely powerful but also notoriously complex (often called the "PL/I" of its generation).
    

## 18. An Imperative-Based OO Language: Java (Early 1990s)

- **Designer:** Sun Microsystems (led by James Gosling).
    
- **Original Goal:** To be a simple, reliable language for embedded electronic devices (like cable TV boxes).
    
- **The Pivot:** Its true success came with the rise of the World Wide Web.
    
- **Core Philosophy:** "Write Once, Run Anywhere."
    
    - Java is compiled to an intermediate **"bytecode,"** not machine code.
        
    - This bytecode runs on a **Java Virtual Machine (JVM)**, a software-based computer.
        
    - This made Java programs **portable**; the same bytecode file could run on Windows, Mac, and Linux.
        
- **Design:** Based on C++ but "simplified" and made safer:
    
    - **No pointer arithmetic,** `structs`, or `unions`.
        
    - **Supports only OOP** (all code must be in a class).
        
    - **Automatic garbage collection** (no manual memory management).
        
- **Evaluation:** Java's portability and safety made it one of the most popular languages in the world, dominating enterprise-scale server applications, Android app development, and early web "applets."
    

## 19. Scripting Languages (1990s)

Scripting languages are typically interpreted, dynamically typed, and designed for "gluing" other systems together.

- **Perl:** Became the "duct tape of the Internet." It combined powerful text processing (from SNOBOL/regex) with system administration capabilities, making it the dominant language for **CGI programming** (processing web forms) in the 90s.
    
- **JavaScript:** The language of the web browser. It is used on the **client-side** to make web pages interactive (popups, form validation, animations). It is now also used on the server-side (Node.js).
    
- **PHP:** A **server-side** scripting language. PHP code is embedded in HTML. When a user requests the page, the server executes the PHP code (e.g., to fetch database results) and embeds the results in the HTML, sending a dynamic page to the user.
    
- **Lua:** A very small, fast, and easily embeddable scripting language. Its primary use is as an **embedded scripting language** in other applications, most notably video games (e.g., _World of Warcraft_). Its one data structure is the "table."
    

## 20. The Flagship .NET Language: C# (2000)

- **Designer:** Microsoft.
    
- **The Context:** C# (C-Sharp) is Microsoft's answer to Java.
    
- **The Platform:** It is the primary language for the **.NET Platform**, which (like the JVM) is a software-based runtime environment called the **Common Language Runtime (CLR)**.
    
- **Design:** Based heavily on C++ and Java, but with additions (like `properties`, `delegates`, and `events`) to make it ideal for component-based development in the Windows ecosystem. It has evolved rapidly and is a major, modern language.
    

## 21. Markup/Programming Hybrid Languages

These are languages that mix descriptive markup (like HTML) with programming logic.

- **XML/XSLT:**
    
    - **XML (eXtensible Markup Language):** A language for _describing data_ (a "metamarkup" language).
        
    - **XSLT (eXtensible Stylesheet Language Transformation):** A language for _transforming_ an XML document into another format (like HTML for display). It is a functional-style language with looping and conditional constructs.
        
- **JSP (JavaServer Pages):**
    
    - This is Java's answer to PHP. It allows a web developer to write a standard HTML page and embed Java code inside special `<% ... %>` tags. The server executes the Java code to generate dynamic content.
        

## Summary

The evolution of programming languages shows a clear trend:

1. **Increasing Abstraction:** Moving from machine code to pseudocodes, to compiled languages, to functional and object-oriented paradigms. Each step hides more of the machine's complexity.
    
2. **Specialization:** Different problems demand different tools. Fortran for numbers, COBOL for business data, LISP for AI, C for systems, and scripting languages for the web.
    
3. **Cross-Pollination:** Ideas from one language (like ALGOL's block structure or SIMULA's classes) are constantly borrowed, refined, and incorporated into the next generation.