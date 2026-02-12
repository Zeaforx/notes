### **Question 1**

**When is a rule said to be recursive in BNF? Give a simple example using `<ident_list>`.**

- **Definition:** A rule in BNF (Backus-Naur Form) is said to be **recursive** if the non-terminal symbol on the Left-Hand Side (LHS) of the rule also appears on the Right-Hand Side (RHS) of the rule. This allows the grammar to generate lists, sequences, or nested structures of arbitrary length.
    
- **Example using `<ident_list>`:**
    
    Plaintext
    
    ```
    <ident_list> ::= <identifier>
    <ident_list> ::= <identifier>, <ident_list>
    ```
    
    _Explanation:_ The second rule is recursive because `<ident_list>` appears on both the left and right sides. This allows you to create a list like "a, b, c" by repeatedly applying the rule.
    

---

### **Question 2**

**Derive the sentence `A = B + C * A` using the grammar/production rule below using the leftmost and rightmost derivation separately.**

_(Note: The specific grammar rules were cut off in the image. I have used the standard Operator Precedence grammar commonly used in CS courses to solve this, treating `*` as having higher precedence than `+`.)_

**Assumed Grammar:**

1. `S -> <id> = <expr>`
    
2. `<expr> -> <expr> + <term> | <term>`
    
3. `<term> -> <term> * <factor> | <factor>`
    
4. `<factor> -> ( <expr> ) | <id>`
    
5. `<id> -> A | B | C`
    

**A. Leftmost Derivation** (Always replace the _leftmost_ non-terminal symbol first)

1. `S` → `<id> = <expr>`
    
2. → `A = <expr>`
    
3. → `A = <expr> + <term>`
    
4. → `A = <term> + <term>`
    
5. → `A = <factor> + <term>`
    
6. → `A = <id> + <term>`
    
7. → `A = B + <term>`
    
8. → `A = B + <term> * <factor>`
    
9. → `A = B + <factor> * <factor>`
    
10. → `A = B + <id> * <factor>`
    
11. → `A = B + C * <factor>`
    
12. → `A = B + C * <id>`
    
13. → `A = B + C * A`
    

**B. Rightmost Derivation** (Always replace the _rightmost_ non-terminal symbol first)

1. `S` → `<id> = <expr>`
    
2. → `<id> = <expr> + <term>`
    
3. → `<id> = <expr> + <term> * <factor>`
    
4. → `<id> = <expr> + <term> * <id>`
    
5. → `<id> = <expr> + <term> * A`
    
6. → `<id> = <expr> + <factor> * A`
    
7. → `<id> = <expr> + <id> * A`
    
8. → `<id> = <expr> + C * A`
    
9. → `<id> = <term> + C * A`
    
10. → `<id> = <factor> + C * A`
    
11. → `<id> = <id> + C * A`
    
12. → `<id> = B + C * A`
    
13. → `A = B + C * A`
    

---

### **Question 3**

**The study of programming language concepts is valuable for some important reasons. Identify five (5) of these reasons and explain briefly.**

1. **Increased capacity to express ideas:** Understanding the underlying concepts of languages (like recursion or associative arrays) allows a programmer to express complex algorithms even in languages that don't natively support those features, by simulating them.
    
2. **Improved background for choosing appropriate languages:** Knowledge of different language constructs helps a programmer evaluate which language is best suited for a specific task (e.g., choosing C for system programming vs. Python for data analysis).
    
3. **Increased ability to learn new languages:** Once you understand the fundamental concepts (types, scopes, control structures), learning a new language becomes mostly a matter of learning new syntax, rather than learning how to program from scratch.
    
4. **Better understanding of the significance of implementation:** Understanding how language features are implemented (e.g., how arrays are stored in memory) allows programmers to write more efficient code and use resources more effectively.
    
5. **Better use of languages that are already known:** Studying concepts often reveals obscure or misunderstood features in languages a programmer already uses, allowing them to utilize the full power of the language.
    

---

### **Question 4**

**Readability, writability and reliability are amongst the most important criteria for evaluating programming languages. Discuss these criteria briefly.**

- **Readability:** This refers to the ease with which programs can be read and understood by humans. A readable language has a clear syntax, consistent structure, and supports meaningful variable names. High readability lowers maintenance costs.
    
- **Writability:** This is a measure of how easily a language can be used to create programs for a given problem domain. It depends on factors like simplicity, orthogonality (a small set of primitive constructs can be combined in relatively small ways), and expressivity (ability to define complex operations concisely).
    
- **Reliability:** A language is considered reliable if it performs to its specifications under all conditions. It is heavily influenced by type checking (detecting errors at compile time), exception handling (dealing with runtime errors gracefully), and readability (easier to read code is easier to debug).