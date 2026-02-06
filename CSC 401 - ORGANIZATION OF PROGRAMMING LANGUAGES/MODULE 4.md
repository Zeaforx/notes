# Chapter 4: Lexical and Syntax Analysis

## Technical Study Guide & Implementation Resource

### 4.1 Introduction

The syntax analyzer (parser) is the heart of a compiler. It drives other components like semantic analysis and code generation.

- **Context:** Syntax analyzers are based on **Context-Free Grammars (BNF)**.
    
- **Separation of Duties:** Compilation is strictly divided into **Lexical Analysis** (low-level pattern matching) and **Syntax Analysis** (high-level structural analysis).
    

**Why separate Lexical and Syntax Analysis?**

1. **Simplicity:** Removes low-level details (like reading characters and buffering) from the complex parser.
    
2. **Efficiency:** Lexical analysis takes a significant portion of compile time; optimizing a separate, simple lexer is easier.
    
3. **Portability:** The lexer handles platform-dependent input (files/buffers), allowing the parser to remain platform-independent.
    

### 4.2 Lexical Analysis

**Core Concepts:**

- **Lexeme:** The logical grouping of characters in the source code (e.g., `result`, `100`, `=`).
    
- **Token:** The internal category code assigned to a lexeme (e.g., `IDENT`, `INT_LIT`, `ASSIGN_OP`).
    
- **Pattern Matching:** The lexer uses a state machine (Finite Automaton) to recognize patterns.
    

#### Implementation: C-Based Lexical Analyzer

The following code implements a simple state-transition logic to recognize arithmetic expressions.

```
/* front.c - A lexical analyzer system for simple arithmetic expressions */
#include <stdio.h>
#include <ctype.h>

/* Character Classes */
#define LETTER 0
#define DIGIT 1
#define UNKNOWN 99

/* Token Codes */
#define INT_LIT 10
#define IDENT 11
#define ASSIGN_OP 20
#define ADD_OP 21
#define SUB_OP 22
#define MULT_OP 23
#define DIV_OP 24
#define LEFT_PAREN 25
#define RIGHT_PAREN 26

/* Global Variables */
int charClass;
char lexeme[100];
char nextChar;
int lexLen;
int token;
int nextToken;
FILE *in_fp;

/* Function Declarations */
void addChar();
void getChar();
void getNonBlank();
int lex();

/* Utility: Add nextChar to lexeme */
void addChar() {
    if (lexLen <= 98) {
        lexeme[lexLen++] = nextChar;
        lexeme[lexLen] = 0;
    } else {
        printf("Error - lexeme is too long \n");
    }
}

/* Utility: Get next char and determine class */
void getChar() {
    if ((nextChar = getc(in_fp)) != EOF) {
        if (isalpha(nextChar))
            charClass = LETTER;
        else if (isdigit(nextChar))
            charClass = DIGIT;
        else 
            charClass = UNKNOWN;
    } else {
        charClass = EOF;
    }
}

/* Utility: Skip whitespace */
void getNonBlank() {
    while (isspace(nextChar))
        getChar();
}

/* Utility: Lookup operators and parentheses */
int lookup(char ch) {
    switch (ch) {
        case '(': addChar(); nextToken = LEFT_PAREN; break;
        case ')': addChar(); nextToken = RIGHT_PAREN; break;
        case '+': addChar(); nextToken = ADD_OP; break;
        case '-': addChar(); nextToken = SUB_OP; break;
        case '*': addChar(); nextToken = MULT_OP; break;
        case '/': addChar(); nextToken = DIV_OP; break;
        default: addChar(); nextToken = EOF; break;
    }
    return nextToken;
}

/* MAIN LEXICAL ANALYZER FUNCTION */
int lex() {
    lexLen = 0;
    getNonBlank();

    switch (charClass) {
        /* Parse Identifiers */
        case LETTER:
            addChar();
            getChar();
            while (charClass == LETTER || charClass == DIGIT) {
                addChar();
                getChar();
            }
            nextToken = IDENT;
            break;

        /* Parse Integer Literals */
        case DIGIT:
            addChar();
            getChar();
            while (charClass == DIGIT) {
                addChar();
                getChar();
            }
            nextToken = INT_LIT;
            break;

        /* Parse Parentheses and Operators */
        case UNKNOWN:
            lookup(nextChar);
            getChar();
            break;

        /* End of File */
        case EOF:
            nextToken = EOF;
            lexeme[0] = 'E'; lexeme[1] = 'O'; lexeme[2] = 'F'; lexeme[3] = 0;
            break;
    }
    printf("Next token is: %d, Next lexeme is %s\n", nextToken, lexeme);
    return nextToken;
}
```

#### Logic Breakdown

1. **Character Classification:** `getChar()` reads input and assigns a `charClass` (LETTER, DIGIT, or UNKNOWN).
    
2. **State Transition (The `lex()` function):**
    
    - If `LETTER`: It enters the **Identifier** state, consuming characters until a non-alphanumeric char is found.
        
    - If `DIGIT`: It enters the **Integer Literal** state, consuming digits.
        
    - If `UNKNOWN`: It assumes the character is an operator or delimiter and calls `lookup()` to assign the specific token code.
        
3. **Output:** It produces a pair: `(Token Code, Lexeme String)`.
    

### 4.3 The Parsing Problem

#### 4.3.1 Goals and Categories

- **Goal:** Determine if input is syntactically correct and build a Parse Tree.
    
- **Categories:**
    
    1. **Top-Down:** Builds tree from Root $\rightarrow$ Leaves. Corresponds to a **Leftmost Derivation**.
        
    2. **Bottom-Up:** Builds tree from Leaves $\rightarrow$ Root. Corresponds to the reverse of a **Rightmost Derivation**.
        

#### 4.3.4 Complexity of Parsing

|   |   |   |
|---|---|---|
|**Algorithm Type**|**Complexity**|**Usage**|
|**General CFG Parsers**|$O(n^3)$|Too slow for practical use. Theoretical only.|
|**Compiler Parsers (LL/LR)**|$O(n)$|Standard for all commercial compilers. Requires using a subset of all grammars.|

### 4.4 Recursive-Descent Parsing (Top-Down)

Recursive Descent is a direct implementation of an EBNF grammar. Every Non-Terminal in the grammar gets its own subroutine.

#### 4.4.1 Trace: Recursive Descent

**Input:** `(sum + 47) / total` **Grammar:** Standard arithmetic expression (Term/Factor).

|   |   |   |   |
|---|---|---|---|
|**Step**|**Current Token**|**Procedure Entry/Exit**|**Logic**|
|1|`(`|Enter `<expr>`|Start symbol called.|
|2|`(`|Enter `<term>`|`<expr>` calls `<term>`.|
|3|`(`|Enter `<factor>`|`<term>` calls `<factor>`.|
|4|`sum`|Enter `<expr>`|`<factor>` sees `(`, consumes it, recurses to `<expr>`.|
|5|`sum`|Enter `<term>`|... recurses to `<term>`.|
|6|`sum`|Enter `<factor>`|... recurses to `<factor>`.|
|7|`+`|Exit `<factor>`|`<factor>` identifies `sum` (IDENT). Returns.|
|8|`+`|Exit `<term>`|`<term>` sees `+` (not `*` or `/`). Returns.|
|9|`47`|Enter `<term>`|`<expr>` sees `+`, calls `<term>` for RHS.|
|10|`47`|Enter `<factor>`|`<term>` calls `<factor>`.|
|11|`)`|Exit `<factor>`|`<factor>` identifies `47` (INT_LIT). Returns.|
|12|`)`|Exit `<term>`|Returns.|
|13|`/`|Exit `<expr>`|Consumes `)`, returns.|
|14|`total`|Enter `<factor>`|Processing division RHS.|
|15|`EOF`|Exit `<factor>`|Identifies `total`.|

#### 4.4.2 The LL Grammar Class (Algorithms)

To use Recursive Descent (LL), the grammar must be free of **Left Recursion** and pass the **Pairwise Disjointness** test.

##### Algorithm Card 1: Removing Direct Left Recursion

**Problem:** A rule like $A \rightarrow A + B$ causes an infinite loop in recursive descent because function `A()` calls `A()` immediately.

**The Transformation:** Given a rule in the format:  

$$A \rightarrow A\alpha \mid \beta$$

_(Where_ $\beta$ _does not start with_ $A$_)_

Replace it with two rules:

1. $$A \rightarrow \beta A'$$
2. $$A' \rightarrow \alpha A' \mid \epsilon$$

**Example:** _Original:_ $E \rightarrow E + T \mid T$ _Mapped:_ $\alpha = +T$, $\beta = T$ _Result:_  

$$E \rightarrow TE'$$$$E' \rightarrow +TE' \mid \epsilon$$

##### Algorithm Card 2: Pairwise Disjointness Test

**Problem:** The parser must decide which RHS to choose based _only_ on the next input token. **The Test:** For every non-terminal $A$ with multiple RHS options ($A \rightarrow \alpha_1 \mid \dots \mid \alpha_n$): The set of possible first terminal characters for each option must not overlap.

$$FIRST(\alpha_i) \cap FIRST(\alpha_j) = \emptyset$$

**Example:** $A \rightarrow aB \mid bC$  

- $FIRST(aB) = \{a\}$  
    
- $FIRST(bC) = \{b\}$  
    
- $\{a\} \cap \{b\} = \emptyset$ $\rightarrow$ **Passes Test.**
    

$A \rightarrow aB \mid aC$  

- Intersection is $\{a\}$. **Fails Test** (Parser doesn't know which path to take seeing 'a').
    

##### Algorithm Card 3: Left Factoring

**Problem:** Fixing a grammar that fails the Pairwise Disjointness test. **The Transformation:** Factor out the common prefix.

**Original:**  

$$<variable> \rightarrow \text{identifier} \mid \text{identifier } [\text{expression}]$$

_(Both start with `identifier`)_

**Factored:**  

$$<variable> \rightarrow \text{identifier } <new>$$$$<new> \rightarrow \epsilon \mid [\text{expression}]$$

### 4.5 Bottom-Up Parsing (LR)

#### 4.5.1 Core Concepts

- **Handle:** The specific substring in the current form that matches a RHS rule and constitutes the correct step to reduce to get the previous step in the derivation.
    
- **Phrase:** Leaves of a partial parse tree rooted at one internal node.
    
- **Simple Phrase:** A phrase that takes only a single derivation step (a direct leaf-to-node connection). **The handle is the leftmost simple phrase.**
    

#### 4.5.2 Shift-Reduce Logic

Bottom-up parsers use a stack.

1. **Shift:** Move next input token onto the stack.
    
2. **Reduce:** If the top of the stack matches a Handle (RHS of a rule), pop it and push the LHS non-terminal.
    

#### 4.5.3 LR Parsers

LR (Left-to-right, Rightmost derivation) parsers use a **Parsing Table** consisting of:

1. **ACTION:** Shift, Reduce, Accept, or Error (based on Input vs State).
    
2. **GOTO:** Determines new state after a reduction (based on Stack State vs Non-Terminal).
    

**Advantages:**

1. Works for a larger class of grammars than LL.
    
2. Detects syntax errors as early as theoretically possible.
    
3. Can handle Left Recursion.
    

**Trace: LR Parsing** _Input:_ `id + id * id`

|   |   |   |   |
|---|---|---|---|
|**Stack**|**Input**|**Action**|**Explanation**|
|`0`|`id + id * id $`|Shift 5|Shift `id` (state 5) onto stack.|
|`0 id 5`|`+ id * id $`|Reduce 6|`id` reduces to `F`. GOTO[0,F] = 3.|
|`0 F 3`|`+ id * id $`|Reduce 4|`F` reduces to `T`. GOTO[0,T] = 2.|
|`0 T 2`|`+ id * id $`|Reduce 2|`T` reduces to `E`. GOTO[0,E] = 1.|
|`0 E 1`|`+ id * id $`|Shift 6|Shift `+`.|
|`0 E 1 + 6`|`id * id $`|Shift 5|Shift `id`.|
|`0 E 1 + 6 id 5`|`* id $`|Reduce 6|`id` reduces to `F`.|
|`0 E 1 + 6 F 3`|`* id $`|Reduce 4|`F` reduces to `T`.|
|`0 E 1 + 6 T 9`|`* id $`|Shift 7|Shift `*` (Operator Precedence!).|
|`0 E 1 + 6 T 9 * 7`|`id $`|Shift 5|Shift `id`.|
|`... * 7 id 5`|`$`|Reduce 6|`id` reduces to `F`.|
|`... * 7 F 10`|`$`|Reduce 3|`T * F` reduces to `T`.|
|`0 E 1 + 6 T 9`|`$`|Reduce 1|`E + T` reduces to `E`.|
|`0 E 1`|`$`|Accept|Stack contains Start Symbol. Input empty.|

### Summary

- **Lexical Analysis:** Groups characters into tokens using finite automata.
    
- **Top-Down (LL):** Easy to write by hand (Recursive Descent), requires special grammar handling (No Left Recursion, Left Factoring).
    
- **Bottom-Up (LR):** Hard to write by hand (use tools like yacc), uses Shift-Reduce on a stack, handles a wider range of grammars efficiently ($O(n)$).