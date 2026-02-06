# Student Resource Guide: Describing Syntax and Semantics

**Based on Chapter 3 of the Course Text**

## 3.1 Introduction

### Definition

- **Syntax:** The form of expressions, statements, and program units.
    
- **Semantics:** The meaning of those expressions, statements, and program units.
    

### Theory vs. Practice

Ideally, semantics should follow directly from syntax (the appearance suggests the meaning). While syntax description has a universally accepted notation (Context-Free Grammars/BNF), semantics lacks a single universal notation.

### Why it Matters

- **Implementors:** Need complete, precise descriptions to build correct compilers.
    
- **Users:** Need authoritative references (manuals) to write valid code.
    
- **Language Designers:** Need formal tools to discover ambiguities during the design phase.
    

## 3.2 The General Problem of Describing Syntax

### Core Definitions

- **Sentence:** A string of characters over some alphabet.
    
- **Language:** A set of sentences.
    
- **Lexeme:** The lowest-level syntactic unit (e.g., `sum`, `+`, `begin`).
    
- **Token:** A category of lexemes (e.g., `identifier` is the token for the lexeme `sum`).
    

### 3.2.1 Language Recognizers

A recognition device reads input strings over the alphabet $\Sigma$ and decides whether they belong to language $L$.

- **Context:** The syntax analysis part of a compiler (parser) is a recognizer. It determines if a program is syntactically correct.
    

### 3.2.2 Language Generators

A device that generates sentences of a language.

- **Comparison:** Generators are often more useful for human study than recognizers. By examining the generation rules, a programmer can determine the structure of valid sentences.
    

## 3.3 Formal Methods of Describing Syntax

### 3.3.1 Backus-Naur Form (BNF) and Context-Free Grammars

#### 3.3.1.1 - 3.3.1.3 Fundamentals

**Context-Free Grammars (CFGs)**, developed by Chomsky, and **Backus-Naur Form (BNF)** are nearly identical metalanguages used to describe syntax.

- **Metalanguage:** A language used to describe another language.
    
- **Abstractions (Nonterminals):** Represent syntactic structures, enclosed in brackets (e.g., `<assign>`).
    
- **Terminals:** Lexemes or tokens.
    
- **Rule (Production):** A definition having a Left-Hand Side (LHS) and a Right-Hand Side (RHS).
    
      
    
    $$\text{<LHS>} \to \text{RHS}$$

**Example Rule:**

```
<assign> -> <var> = <expression>
```

#### 3.3.1.4 Describing Lists

BNF does not use ellipses (`...`). Variable-length lists are described using **recursion**.

**Example (Recursive List):**

```
<ident_list> -> identifier
              | identifier, <ident_list>
```

#### 3.3.1.5 Grammars and Derivations

A **derivation** is a sequence of rule applications, starting with a start symbol, ending with a sentence (only terminals).

- **Sentential Form:** Any string in the derivation (contains terminals and/or nonterminals).
    
- **Leftmost Derivation:** The leftmost nonterminal is replaced at each step.
    

**Example Derivation (Leftmost):**

```
<program> => begin <stmt_list> end
          => begin <stmt> end
          => begin A = B + C end
```

#### 3.3.1.6 Parse Trees

A hierarchical graphical representation of a derivation.

- **Root:** Start symbol.
    
- **Internal Nodes:** Nonterminals.
    
- **Leaves:** Terminals.
    

<Insert Diagram: Figure 3.1 - A parse tree for A = B * (A + C)>

#### 3.3.1.7 Ambiguity

A grammar is **ambiguous** if it generates a sentential form that has two or more distinct parse trees.

- **Consequence:** Compilers often base semantics (code generation) on the parse tree. Ambiguity prevents unique semantic interpretation.
    
- **Detection:** If a grammar generates a sentence with two distinct leftmost derivations, it is ambiguous.
    

<Insert Diagram: Figure 3.2 - Two distinct parse trees for A = B + C * A>

#### 3.3.1.8 Operator Precedence

Precedence determines the order of evaluation (e.g., multiplication before addition).

- **Implementation in BNF:** Assign different precedence levels to different nonterminals. Operators with _higher_ precedence are placed _lower_ in the parse tree (further from the start symbol).
    

**Unambiguous Expression Grammar (Standard Precedence):**

```
<expr>   -> <expr> + <term> | <term>
<term>   -> <term> * <factor> | <factor>
<factor> -> (<expr>) | <id>
```

_Note: `<factor>` is lower than `<term>`, so `*` (in term) is evaluated before `+` (in expr)._

#### 3.3.1.9 Associativity of Operators

Determines evaluation order for operators of the same precedence (e.g., `A - B - C`).

- **Left Associativity:** Achieved via **Left Recursion** (e.g., `<expr> -> <expr> + <term>`).
    
- **Right Associativity:** Achieved via **Right Recursion** (e.g., `<factor> -> <exp> ** <factor>`).
    

#### 3.3.1.10 An Unambiguous Grammar for if-then-else

The "Dangling Else" problem: `if x then if y then S1 else S2`. Does the `else` belong to the first or second `if`?

- **Standard Rule:** `else` matches the nearest previous unmatched `then`.
    
- **BNF Solution:** Distinguish between matched and unmatched statements.
    

```
<stmt> -> <matched> | <unmatched>
<matched> -> if <logic_expr> then <matched> else <matched>
           | any non-if statement
<unmatched> -> if <logic_expr> then <stmt>
             | if <logic_expr> then <matched> else <unmatched>
```

### 3.3.2 Extended BNF (EBNF)

Extensions to BNF to improve readability (not descriptive power).

1. **Optional parts:** Placed in brackets `[]`.
    
    - `if (<expr>) <stmt> [else <stmt>]`
        
2. **Repetitions (0 or more):** Placed in braces `{}`.
    
    - `<ident_list> -> <ident> {, <ident>}`
        
3. **Multiple Choice:** Placed in parentheses `()` separated by `|`.
    
    - `<term> -> <term> (* | / | %) <factor>`
        

### 3.3.3 Grammars and Recognizers

Tools like `yacc` (Yet Another Compiler Compiler) can algorithmically construct a syntax analyzer (parser) from a given context-free grammar.

## 3.4 Attribute Grammars

### 3.4.1 Static Semantics

Language rules that are difficult or impossible to describe with BNF (e.g., type compatibility, "variables must be declared before use"). These are checked at compile time.

### 3.4.3 Attribute Grammars Defined

An extension of CFGs designed by Knuth to describe syntax and static semantics.

- **Attributes** $A(X)$**:** Associated with grammar symbol $X$.
    
    - **Synthesized (**$S(X)$**):** Pass information **up** the parse tree.
        
    - **Inherited (**$I(X)$**):** Pass information **down** or **across** the tree.
        
- **Semantic Functions:** Associated with rules. Define how attribute values are computed.
    
- **Predicate Functions:** Boolean expressions. If false, it indicates a syntax/static semantic error.
    

### 3.4.5 Example: Type Checking

**Rule:**

```
<expr> -> <var>[2] + <var>[3]
```

**Semantic Rule (Type Logic):**

```
<expr>.actual_type <- if (<var>[2].actual_type = int) and (<var>[3].actual_type = int)
                      then int
                      else real
```

**Predicate:**

```
<expr>.actual_type == <expr>.expected_type
```

### 3.4.6 Computing Attribute Values

The process of "decorating" the parse tree requires an evaluation order (dependency graph).

1. **Intrinsic Attributes:** Values determined outside the tree (e.g., from the symbol table).
    
2. Synthesized attributes are computed from children.
    
3. Inherited attributes are computed from parents/siblings.
    

## 3.5 Describing the Meanings of Programs: Dynamic Semantics

### 3.5.1 Operational Semantics

Describes meaning by specifying the effects of running a statement on a machine.

- **Mechanism:** Uses an **intermediate language** and a **virtual machine**.
    
- **State:** The collection of values in the machine's storage.
    
- **Usage:** Good for implementors.
    
- **Drawback:** Can be complex or circular if the intermediate language is not rigorously defined (e.g., VDL for PL/I).
    

### 3.5.2 Denotational Semantics

Describes meaning by mapping syntactic entities to mathematical objects (recursive function theory).

#### 3.5.2.1 Fundamentals

- **Syntactic Domain:** The set of valid programs/statements.
    
- **Semantic Domain:** Mathematical objects (e.g., Integers $N$, Boolean values, Functions).
    
- **Mapping Function:** Maps syntax to semantics.
    

**Example: Binary Numbers**

  

$$ M_{bin}(\text{'0'}) = 0 $$$$ M_{bin}(\text{'1'}) = 1 $$$$ M_{bin}(<bin\_num> \text{'0'}) = 2 * M_{bin}(<bin\_num>) $$$$ M_{bin}(<bin\_num> \text{'1'}) = 2 * M_{bin}(<bin\_num>) + 1 $$

#### 3.5.2.2 The State of a Program

Defined as a set of ordered pairs (variable name, value).

  

$$ s = \{<i_1, v_1>, <i_2, v_2>, \dots, <i_n, v_n>\} $$

Function `VARMAP(i, s)` retrieves the value $v$ of variable $i$ in state $s$.

#### 3.5.2.5 Logical Pretest Loops

Loops are defined via recursion.

  

$$ M_l(\text{while } B \text{ do } L, s) \Delta= $$$$ \text{if } M_b(B, s) == \text{false then } s $$$$ \text{else } M_l(\text{while } B \text{ do } L, M_s(L, s)) $$

### 3.5.3 Axiomatic Semantics

Based on mathematical logic (predicate calculus). Primarily used for **program verification** (correctness proofs).

#### 3.5.3.1 Assertions

- **Precondition** $\{P\}$**:** Constraints on variables _before_ execution.
    
- **Postcondition** $\{Q\}$**:** Constraints on variables _after_ execution.
    
- **Format:** $\{P\} S \{Q\}$  
    

#### 3.5.3.2 Weakest Precondition (wp)

The least restrictive precondition that guarantees the postcondition will be valid.

#### 3.5.3.3 Assignment Statements (Axiom)

To find the precondition for $x = E$ and postcondition $Q$, replace all instances of $x$ in $Q$ with $E$.

  

$$ P = Q_{x \to E} $$

**Example:**

Statement: `a = b / 2 - 1`

Postcondition: `{a < 10}`

Weakest Precondition: `b / 2 - 1 < 10` $\Rightarrow$ `b < 22`.

#### 3.5.3.4 Sequences (Inference Rule)

$$ \frac{\{P1\} S1 \{P2\}, \{P2\} S2 \{P3\}}{\{P1\} S1; S2 \{P3\}} $$

To find the precondition of a sequence, the precondition of the second statement becomes the postcondition of the first.

#### 3.5.3.5 Selection (Inference Rule)

For `if B then S1 else S2`:

  

$$ \frac{\{B \land P\} S1 \{Q\}, \{(\neg B) \land P\} S2 \{Q\}}{\{P\} \text{if } B \text{ then } S1 \text{ else } S2 \{Q\}} $$

#### 3.5.3.6 Logical Pretest Loops (Inference Rule)

Requires a **Loop Invariant (**$I$**)**.

  

$$ \frac{\{I \land B\} S \{I\}}{\{I\} \text{while } B \text{ do } S \text{ end } \{I \land \neg B\}} $$

**Requirements for a Correct Loop Verification:**

1. $P \Rightarrow I$ (Precondition implies Invariant)
    
2. $\{I \land B\} S \{I\}$ (Invariant is maintained by the loop body)
    
3. $(I \land \neg B) \Rightarrow Q$ (Invariant + exit condition implies Postcondition)
    
4. The loop terminates.
    

**Total Correctness:** Verification that includes termination proof.

**Partial Correctness:** Verification assuming termination.

## End of Chapter Materials

### Summary

- **BNF/CFGs:** Standard for syntax, naturally describe hierarchy (parse trees).
    
- **Attribute Grammars:** Extend CFGs to handle static semantics (typing).
    
- **Operational Semantics:** Execution on an ideal machine.
    
- **Denotational Semantics:** Mapping to mathematical functions.
    
- **Axiomatic Semantics:** Logic-based, used for proofs.
    

### Key Problem Set Concepts

- **Ambiguity Proofs:** Demonstrating two parse trees for one string.
    
- **Grammar Conversion:** BNF to EBNF and vice versa.
    
- **Computing Weakest Preconditions:** Applying the axioms for assignment, sequence, and selection.
    
- **Loop Invariants:** Identifying the mathematical relationship maintained through iterations.