 Course Notes: Chapter 3 - Describing Syntax and Semantics

## 1. Introduction

This chapter covers the methods used to formally describe the **syntax** (the form and structure) and **semantics** (the meaning) of programming languages.

- **Syntax:** What does a valid program _look_ like?
    
- **Semantics:** What does a valid program _do_?
    

## 2. The General Problem of Describing Syntax

### 2.1. Key Terminology

- **Sentence:** A string of characters over some alphabet (e.g., a complete, valid line of code like `x = a + b;`).
    
- **Language:** The set of all valid sentences (e.g., the set of all possible valid C++ programs).
    
- **Lexeme:** The lowest-level syntactic unit of a language. These are the "words" of the language.
    
    - _Examples:_ `*`, `sum`, `begin`, `(`, `10.5`
        
- **Token:** A category of lexemes. This is the abstract category that a lexeme belongs to.
    
    - _Examples:_ `identifier`, `operator`, `keyword`, `left_paren`, `float_literal`
        

| **Lexeme** | **Token**         |
| ---------- | ----------------- |
| `sum`      | `identifier`      |
| `while`    | `keyword`         |
| `+`        | `operator`        |
| `5`        | `integer_literal` |

### 2.2. Formal Definition of Languages

There are two main ways to formally define a language's syntax:

1. **Recognizers (Syntax Analysis):**
    
    - A device (like the _syntax analysis_ part of a compiler, also known as a parser) that reads an input string and decides if it belongs to the language.
        
    - It _recognizes_ valid sentences.
        
    - **Analogy:** An English teacher who reads a sentence and tells you "Yes, this is grammatically correct" or "No, this is not."
        
2. **Generators (Grammars):**
    
    - A device or set of rules that _generates_ all the valid sentences of a language.
        
    - If you can generate a sentence using these rules, it is syntactically correct.
        
    - **Analogy:** A set of grammar rules (like "A sentence is a noun phrase followed by a verb phrase") that you can follow to _create_ new, valid sentences.
        

## 3. Formal Methods of Describing Syntax: BNF

The most common method for generating a language's syntax is a **Context-Free Grammar (CFG)**, developed by Noam Chomsky. A popular notation for CFGs is **Backus-Naur Form (BNF)**.

- **Context-Free Grammars (CFGs):** Language generators developed in the 1950s to describe the syntax of natural languages.
    
- **Backus-Naur Form (BNF):** Invented by John Backus to describe the syntax of the Algol 58 programming language. BNF and CFGs are equivalent in power.
    

### 3.1. BNF Fundamentals

BNF is a set of _derivation rules_ (also called _productions_).

- **Nonterminals (Abstractions):** These are the syntactic variables that represent classes of structures. They are typically enclosed in angle brackets `<...>`. Example: `<expr>`, `<stmt>`, `<program>`.
    
- **Terminals:** These are the lexemes or tokens of the language. They are the actual "words" that appear in the code. Example: `if`, `+`, `a`, `(`.
    
- **Rules:** A rule has:
    
    - A **Left-Hand Side (LHS):** A single nonterminal.
        
    - A **Right-Hand Side (RHS):** A string of terminals and/or nonterminals.
        
    - The symbol `::=` (or `->`) means "is defined as".
        
    - The symbol `|` means "or" (alternation).
        

### 3.2. Example BNF Rules

**1. A simple assignment statement:**

```
<assign> ::= <var> = <expr>
```

This rule states: "An _assignment_ is defined as a _variable_, followed by the terminal `=`, followed by an _expression_."

**2. An `if` statement:**

```
<if_stmt> ::= if ( <logic_expr> ) <stmt>
            | if ( <logic_expr> ) <stmt> else <stmt>
```

This rule shows alternation: "An _if statement_ is defined as either..."

- "...the terminal `if`, a `(`, a _logic expression_, a `)`, and a _statement_."
    
- "...OR the terminal `if`, a `(`, a _logic expression_, a `)`, a _statement_, the terminal `else`, and another _statement_."
    

3. Describing Lists (using Recursion):

BNF uses recursion to define lists of items (e.g., a list of identifiers).

```
<ident_list> ::= <identifier>
              | <identifier> , <ident_list>
```

This is a recursive definition: "An _identifier list_ is either..."

- "...a single _identifier_." (This is the **base case**).
    
- "...OR an _identifier_, followed by a comma, followed by another _identifier list_." (This is the **recursive step**).
    

This allows you to generate lists of any length: `a`, `a, b`, `a, b, c`, etc.

### 3.3. Derivations and Parse Trees

- **Derivation:** A sequence of rule applications that starts with the main nonterminal (e.g., `<program>`) and ends with a string of only terminal symbols.
    
- **Sentential Form:** Any string of symbols (terminals and nonterminals) that appears in a derivation.
    
- **Sentence:** The final sentential form in a derivation that contains _only_ terminal symbols.
    

**Example Grammar:**

```
<program> ::= <stmts> 
<stmts>   ::= <stmt> | <stmt> ; <stmts>
<stmt>    ::= <var> = <expr>
<expr>    ::= <term> + <term> | <term>
<term>    ::= <var> | const
<var>     ::= a | b | c
```

**Example Derivation (for the sentence `a = b + const`):**

1. `<program>`
    
2. `=> <stmts>`
    
3. `=> <stmt>`
    
4. `=> <var> = <expr>`
    
5. `=> a = <expr>`
    
6. `=> a = <term> + <term>`
    
7. `=> a = <var> + <term>`
    
8. `=> a = b + <term>`
    
9. `=> a = b + const` (This is the final **sentence**)
    

- A **leftmost derivation** is one where the leftmost nonterminal is always the one expanded in the next step (as shown in the example above).
    

Parse Tree:

A parse tree is a hierarchical, graphical representation of a derivation. The root of the tree is the start symbol, the leaves are the terminal symbols, and the interior nodes are nonterminals.

A parse tree for the derivation above:

```
          <program>
              |
           <stmts>
              |
            <stmt>
           /  |  \
       <var>  =  <expr>
         |       /  |  \
         a   <term>  +  <term>
               |         |
             <var>     const
               |
               b
```

### 3.4. Ambiguity in Grammars

A grammar is **ambiguous** if it generates a sentential form that has two or more distinct parse trees. This is a major problem for compilers, because the parse tree dictates the meaning (semantics) of the code.

**Classic Ambiguous Grammar (for `const + const * const`):**

```
<expr> ::= <expr> + <expr>
        | <expr> * <expr>
        | const
```

This grammar allows two different parse trees for `const + const * const`:

**Parse Tree 1 (Addition first)**

```
      <expr>
      /  |  \
   <expr>  *  const
   /  |  \
<expr>  +  <expr>
  |        |
const    const
```

_(Meaning: (const + const) * const)_

**Parse Tree 2 (Multiplication first)**

```
      <expr>
      /  |  \
   <expr>  +  <expr>
     |       /  |  \
   const  <expr>  *  <expr>
            |         |
          const     const
```

_(Meaning: const + (const * const))_

### 3.5. Removing Ambiguity: Precedence and Associativity

Ambiguity is removed by rewriting the grammar to enforce operator **precedence** (which operator goes first) and **associativity** (order for operators of the same precedence).

Unambiguous Grammar (with precedence and associativity):

This grammar enforces that * has higher precedence than +, and that both are left-associative (e.g., a + b + c is parsed as (a + b) + c).

```
<expr> ::= <expr> + <term>   // '+' is left-associative
        | <term>

<term> ::= <term> * <factor>  // '*' is left-associative
        | <factor>

<factor> ::= ( <expr> )
          | const
```

- **Precedence:** Is enforced by creating separate nonterminals (`<expr>`, `<term>`, `<factor>`). Operators with lower precedence (like `+`) are higher in the grammar, and operators with higher precedence (like `*`) are lower.
    
- **Associativity:** Is enforced by the direction of recursion.
    
    - **Left-associativity** (`<expr> ::= <expr> + <term>`) ensures parsing from the left.
        
    - **Right-associativity** (for an operator like exponentiation `^`) would be written as `<factor> ::= <primary> ^ <factor>`.
        

### 3.6. Extended BNF (EBNF)

EBNF adds notation to BNF to make grammars more concise. It does not add more power.

- **Optional Items `[ ... ]`:** Items in square brackets are optional (zero or one).
    
    - _BNF:_ `<if_stmt> ::= if (...) <stmt> | if (...) <stmt> else <stmt>`
        
    - _EBNF:_ `<if_stmt> ::= if (...) <stmt> [ else <stmt> ]`
        
- **Repetition `{ ... }`:** Items in curly braces can be repeated zero or more times.
    
    - _BNF:_ `<ident_list> ::= <identifier> | <identifier> , <ident_list>`
        
    - _EBNF:_ `<ident_list> ::= <identifier> { , <identifier> }`
        
- **Grouping `( ... )`:** Used to group items, often with alternation `|`.
    
    - _EBNF:_ `<term> ::= <factor> ( * | / | % ) <factor>`
        

## 4. Static Semantics

CFGs and BNF can't describe all of a language's syntax rules.

- **Static Semantics** are rules that are checked at _compile time_ but are difficult or impossible to express with a CFG. These rules often involve context.
    
- **Examples:**
    
    1. **Declaration before use:** A variable must be declared before it is used. A CFG can't track which variables have been declared.
        
    2. **Type checking:** The types of operands in an expression must be compatible. `10 + "hello"` is syntactically valid according to a BNF, but it is semantically invalid.
        
    3. **Function call parameters:** The number and types of arguments in a function call must match the function's definition.
        

### 4.1. Attribute Grammars (AGs)

**Attribute Grammars** are a formal method for checking static semantics. They work by adding _attributes_ and _rules_ to a CFG.

- An attribute is a property associated with a grammar symbol (a nonterminal in the parse tree).
    
- Attribute values are computed by rules associated with the grammar productions.
    
- **Predicates** (consistency checks) can be added to rules to enforce static semantic constraints.
    

There are two main types of attributes:

1. **Synthesized Attributes (Bottom-Up):**
    
    - The value of an attribute is computed from the attribute values of its _children_ nodes in the parse tree.
        
    - Information flows **up** the tree.
        
    - **Example:** The `actual_type` of an expression. The type of `<expr> -> <term> + <term>` is determined by the types of the two `<term>` children.
        
2. **Inherited Attributes (Top-Down):**
    
    - The value of an attribute is computed from the attribute values of its _parent_ and/or _sibling_ nodes.
        
    - Information flows **down and across** the tree.
        
    - **Example:** The `expected_type` of an expression. In an assignment `<assign> -> <var> = <expr>`, the type of `<var>` (from the symbol table) is passed _down_ to the `<expr>` node as its `expected_type`.
        

**Example:** Type checking for `A = A + B`

**Grammar:**

```
<assign> -> <var> = <expr>
<expr>   -> <var> + <var>
<var>    -> A | B | C
```

**Attributes:**

- `actual_type` (Synthesized): For `<var>` and `<expr>`.
    
- `expected_type` (Inherited): For `<expr>`.
    

**Semantic Rules:**

1. **Production:** `<assign> -> <var> = <expr>`
    
    - **Rule:** `<expr>.expected_type = <var>.actual_type` (Inherited: pass type down)
        
    - **Predicate:** `check_types(<var>.actual_type, <expr>.actual_type)` (Are they compatible?)
        
2. **Production:** `<expr> -> <var1> + <var2>`
    
    - **Rule:** `<expr>.actual_type = common_type(<var1>.actual_type, <var2>.actual_type)` (Synthesized: compute type from children)
        
    - **Predicate:** `check_compatible(<var1>.actual_type, <var2>.actual_type)`
        

**How values are computed (Parse Tree Decoration):**

1. The tree is built (Syntax Analysis).
    
2. A **bottom-up** pass computes all synthesized attributes (e.g., the `actual_type` of all `<var>` nodes from the symbol table).
    
3. A **top-down** pass computes all inherited attributes (e.g., the `expected_type` of `<expr>` is passed down from `<assign>`).
    
4. Another **bottom-up** pass computes the remaining synthesized attributes (e.g., the `actual_type` of `<expr>` is computed from its children).
    
5. Predicates are checked. If any fail, a static semantic error is reported.
    

## 5. Dynamic Semantics

**Dynamic Semantics** describes the _meaning_ and _behavior_ of a program as it executes. There are three main approaches:

1. **Operational Semantics**
    
2. **Denotational Semantics**
    
3. **Axiomatic Semantics**
    

### 5.1. Operational Semantics

Describes the meaning of a program by defining how its statements execute on a machine (either a real or a simulated one). The meaning of a statement is the _change it produces in the machine's state_ (memory, registers, etc.).

- **Example:** The meaning of `x = a + b` is the set of machine instructions that:
    
    1. Fetches the value of `a` from memory.
        
    2. Fetches the value of `b` from memory.
        
    3. Adds them.
        
    4. Stores the result in the memory location for `x`.
        
- A **virtual machine** is needed to describe a high-level language. This involves:
    
    1. A translator (to convert source code to the virtual machine's code).
        
    2. A simulator (to run the virtual machine's code).
        
- **Levels:**
    
    - **Natural Operational Semantics:** Describes the _final result_ of an execution.
        
    - **Structural Operational Semantics:** Describes each _individual step_ of the execution.
        
- **Evaluation:**
    
    - **Good:** If used informally (e.g., in language manuals, textbooks). It's intuitive.
        
    - **Bad:** Extremely complex if used formally (e.g., VDL for PL/I). The definition can be machine-dependent and hard to understand.
        

### 5.2. Denotational Semantics

Describes meaning by mapping language constructs to _mathematical objects_ (specifically, functions). It is the most abstract method.

- Developed by Scott and Strachey (1970).
    
- Based on recursive function theory.
    
- The meaning of language constructs is defined _only by the values of the program's variables_.
    
- The **state** (or _store_) of a program is a mathematical function that maps variable names to their values: `s: Variables -> Values`.
    

**Denotational Mappings (Semantic Functions):**

- **Expressions:** The meaning of an expression is a function that takes the _current state_ and returns a _value_.
    
    - `M_e(<expr>, s)`
        
    - Example: `M_e(<E1> + <E2>, s) = M_e(<E1>, s) + M_e(<E2>, s)`
        
- **Assignment Statements:** The meaning of a statement is a function that takes an _old state_ and returns a _new state_.
    
    - `M_s(<stmt>, s)`
        
    - Example: `M_s(<var> = <expr>, s) = s'` where `s'` is a new state function that is identical to `s`, _except_ that `s'(<var>) = M_e(<expr>, s)`.
        
- **Logical Pretest Loops (`while B do S`):**
    
    - This is the most complex. The loop's meaning is defined as the _least fixed point_ of a recursive function.
        
    - This converts iteration (the `while` loop) into recursion (a mathematical function) which is easier to describe with rigor.
        
    - Intuition: The meaning of the while loop W is a function M(W, s) that can be defined recursively:
        
        M(W, s) = if M_b(B, s) == false then s
        
        else M(W, M_s(S, s))
        
    - The "least fixed point" is the mathematical solution to this recursive definition, representing the final state after the loop terminates (or non-termination if it doesn't).
        
- **Evaluation:**
    
    - **Good:** Can be used to prove program correctness, aids language design, and is used in compiler generators.
        
    - **Bad:** Extremely complex and of little use to typical language users or programmers.
        

### 5.3. Axiomatic Semantics

Describes meaning using formal logic (predicate calculus). It does not describe the full execution, but rather what can be _proven_ to be true before and after a statement executes.

- **Original Purpose:** Formal program verification.
    
- **Assertion:** A logical expression stating relationships and constraints among variables.
    
    - **Precondition:** An assertion _before_ a statement.
        
    - **Postcondition:** An assertion _after_ a statement.
        
- **Hoare Triple:** The standard form is **`{P} S {Q}`**
    
    - This means: "If the precondition `{P}` is true before statement `S` executes, then the postcondition `{Q}` will be true after `S` executes (assuming `S` terminates)."
        
- **Weakest Precondition:** The least restrictive precondition that will _guarantee_ the postcondition.
    
    - **Example:** For the statement `a = b + 1` and postcondition `{a > 1}`:
        
        - `{b > 10}` is a valid precondition.
            
        - `{b > 5}` is a valid precondition.
            
        - `{b > 0}` is the **weakest precondition**.
            

**Axioms and Inference Rules:**

1. **Assignment:** `{Q_x->E} x = E {Q}`
    
    - This is an axiom (a fundamental truth). To find the weakest precondition, you take the postcondition `Q` and replace all instances of `x` with the expression `E`.
        
    - **Example:** To find the weakest precondition for `x = x + 1 {x > 5}`:
        
        - Replace `x` in `{x > 5}` with `x + 1`.
            
        - The weakest precondition is `{x + 1 > 5}`, which simplifies to `{x > 4}`.
            
2. **Rule of Consequence:**
    
    - This rule allows you to _strengthen_ a precondition and _weaken_ a postcondition.
        
    - If you know `{P'} S {Q'}` is true, and you can prove that `P => P'` (your P is stronger) and `Q' => Q` (your Q is weaker), then you can conclude `{P} S {Q}`.
        
3. **Sequences:** For a sequence `S1; S2`:
    
    - `{P} S1 {R}` and `{R} S2 {Q}`
        
    - Therefore: `{P} S1; S2 {Q}`
        
    - To prove a sequence, you find an intermediate assertion `R` that is the postcondition of `S1` and the precondition of `S2`.
        
4. **Selection (if-then-else):**
    
    - `{B and P} S1 {Q}` and `{(not B) and P} S2 {Q}`
        
    - Therefore: `{P} if B then S1 else S2 {Q}`
        
    - You must prove that the postcondition `Q` holds for _both_ branches.
        
5. **Loops (while):** `{P} while B do S end {Q}`
    
    - This is the most complex rule and requires finding a **loop invariant (I)**.
        
    - The **Loop Invariant `I`** is an assertion that must satisfy four conditions:
        
        1. `P => I` (The invariant must be true before the loop starts).
            
        2. `{I and B} S {I}` (The invariant must be _preserved_ by the loop body; if it's true at the start of an iteration, it's true at the end).
            
        3. `(I and (not B)) => Q` (When the loop terminates (because `B` is false), the invariant plus the exit condition must imply the final postcondition `Q`).
            
        4. The loop must terminate (this is proven separately).
            
    - The full inference rule is: `{I and B} S {I}` / `{I} while B do S {I and (not B)}`
        

- **Evaluation:**
    
    - **Good:** Excellent tool for correctness proofs and reasoning about programs.
        
    - **Bad:** Difficult to develop all the axioms for a complex language. Not very useful for language users or compiler writers directly.
        

## 6. Summary

- **BNF** and **CFGs** are equivalent meta-languages (languages used to describe other languages) well-suited for describing the _syntax_ of programming languages.
    
- **Attribute Grammars** extend CFGs to describe _static semantics_ (compile-time checks like type-checking) by adding attributes and rules to the parse tree.
    
- **Dynamic Semantics** (meaning) can be described in three primary ways:
    
    - **Operational:** What the program _does_ on a machine (state changes).
        
    - **Denotational:** What the program _is_ as a mathematical function.
        
    - **Axiomatic:** What can be _proven_ to be true about the program.