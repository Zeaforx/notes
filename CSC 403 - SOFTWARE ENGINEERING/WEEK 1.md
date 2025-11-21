## Week 1 Review Questions

Here are some review questions based on the week's topics, along with their answers.

**1. If software engineering is beyond ordinary development, what differentiates a software developer from a software engineer?**

This is a key distinction. Think of it as the difference between a skilled carpenter and an architect who also knows how to build.

- A **Software Developer (or Programmer)** is primarily focused on the _act of coding_. They are experts at taking a set of requirements and translating them into clean, functional code using a specific programming language. Their main role is the "building" or "construction" phase.
    
- A **Software Engineer** is involved in the _entire lifecycle_ of the product. They apply formal engineering principles (analysis, mathematics, and computer science) to the design, development, testing, and maintenance of complex software systems.
    

**Key Differences:**

|Aspect|Software Developer|Software Engineer|
|---|---|---|
|**Scope**|Focused on coding and implementing features.|Oversees the entire process, from idea to retirement.|
|**Process**|Follows the design given to them.|_Creates_ the design, architecture, and testing strategy.|
|**Focus**|"How do I build this feature?"|"Why are we building this?" "What's the most reliable, efficient, and maintainable way to build this entire _system_?"|
|**Analogy**|A skilled carpenter who builds a high-quality staircase.|An architect who designs the entire house, ensures it's structurally sound, manages the project, and also knows how to build the staircase.|

Software engineering is "beyond ordinary development" because it adds a layer of rigorous process, design, and long-term planning to manage the complexity of building large-scale, reliable systems—not just writing individual programs.

**2. Why is there any need for most of the components of software (e.g., design docs, manuals)? Why not just deliver the code?**

Delivering "just the code" is like giving someone a box of car engine parts with no assembly instructions, no driver's manual, and no key. The individual parts might be perfect, but the "product" is useless, dangerous, and impossible to fix.

The different components of the "Software Tree" are necessary to turn raw code into a complete, usable, and maintainable product:

- **Design Documents (Blueprints):** You need these to ensure you build the _right_ thing. Without a plan, you risk the components not fitting together, failing to meet user needs, and creating a system that's impossible to expand.
    
- **Source Code (The Recipe):** This is the core logic. You need it to fix bugs, add new features, or adapt the software for a new platform.
    
- **Executable (The Finished Cake):** This is the actual usable product for the end-user, who doesn't know or care about the source code.
    
- **System Manuals (User & Technical Guides):**
    
    - **User Manuals:** The software is useless if people don't know how to use it.
        
    - **Technical Manuals:** The software is unsupportable if IT staff don't know how to install, configure, or troubleshoot it.
        
- **Installation & Implementation:** The software provides no value if it's just sitting on a developer's hard drive. It must be installed on the user's system and integrated into their workflow.
    

In short, a software _product_ must deliver long-term value. This requires it to be **usable** (manuals), **functional** (executable), and **maintainable** (source code and design docs).

**3. Write a program to solve for the area and perimeter of a parallelogram and use it to differentiate between source code and executable.**

Here is a simple program in Visual Basic (as mentioned in the course notes). This code would be placed inside the "Click" event for a button on a form.

### Part A: The Program

This program assumes you have text boxes named `txtBase`, `txtHeight`, and `txtSide`, a button named `btnCalculate`, and labels named `lblArea` and `lblPerimeter`.

**This is the SOURCE CODE (saved in a `.vb` file):**

```
' This code runs when the user clicks the "btnCalculate" button
Private Sub btnCalculate_Click(sender As Object, e As EventArgs) Handles btnCalculate.Click
    
    ' 1. Get input from the user (from text boxes)
    ' We use Double to allow for decimal numbers
    Dim base As Double
    Dim height As Double
    Dim side As Double

    ' Use TryParse for safety, to avoid crashes if the user enters text
    Double.TryParse(txtBase.Text, base)
    Double.TryParse(txtHeight.Text, height)
    Double.TryParse(txtSide.Text, side)

    ' 2. Perform the calculations
    Dim area As Double = base * height
    Dim perimeter As Double = 2 * (base + side)

    ' 3. Display the output to the user (in labels)
    ' We use .ToString() to convert the number back to text
    lblArea.Text = "Area: " & area.ToString()
    lblPerimeter.Text = "Perimeter: " & perimeter.ToString()

End Sub
```

### Part B: Differentiating Source Code vs. Executable

- **Source Code:**
    
    - The VB code shown above is the **source code**.
        
    - It is a **human-readable** text file (`.vb`). You can open it in Notepad, read it, and understand its logic (e.g., `area = base * height`).
        
    - It is the "recipe." It _describes_ the program but is not the program itself.
        
    - You **cannot run** this file directly. Double-clicking a `.vb` file just opens it in a text editor.
        
- **Executable:**
    
    - After you "Build" or "Compile" this project in Visual Basic, it creates a new file, such as `ParallelogramSolver.exe`. This is the **executable**.
        
    - It is a **machine-readable** binary file. If you open it in Notepad, you will see unreadable symbols and gibberish.
        
    - It is the "finished cake." It is the actual, runnable application built _from_ the recipe.
        
    - This is the file you give to your users. They can **double-click the `.exe` file to run** your program and calculate the area of a parallelogram, even if they don't have Visual Basic installed.

<!-- ... existing content ... -->

### Tool Integration Mechanisms

- The "glue" that makes all the different developer tools (the code editor, the testing tool, the bug tracker) talk to each other to create a smooth workflow.
    

## 3. Week 1 Review Questions

Here are some review questions based on the week's topics, along with their answers.

**1. If software engineering is beyond ordinary development, what differentiates a software developer from a software engineer?**

This is a key distinction. Think of it as the difference between a skilled carpenter and an architect who also knows how to build.

- A **Software Developer (or Programmer)** is primarily focused on the _act of coding_. They are experts at taking a set of requirements and translating them into clean, functional code using a specific programming language. Their main role is the "building" or "construction" phase.
    
- A **Software Engineer** is involved in the _entire lifecycle_ of the product. They apply formal engineering principles (analysis, mathematics, and computer science) to the design, development, testing, and maintenance of complex software systems.
    

**Key Differences:**

|   |   |   |
|---|---|---|
|**Aspect**|**Software Developer**|**Software Engineer**|
|**Scope**|Focused on coding and implementing features.|Oversees the entire process, from idea to retirement.|
|**Process**|Follows the design given to them.|_Creates_ the design, architecture, and testing strategy.|
|**Focus**|"How do I build this feature?"|"Why are we building this?" "What's the most reliable, efficient, and maintainable way to build this entire _system_?"|
|**Analogy**|A skilled carpenter who builds a high-quality staircase.|An architect who designs the entire house, ensures it's structurally sound, manages the project, and also knows how to build the staircase.|

Software engineering is "beyond ordinary development" because it adds a layer of rigorous process, design, and long-term planning to manage the complexity of building large-scale, reliable systems—not just writing individual programs.

**2. Why is there any need for most of the components of software (e.g., design docs, manuals)? Why not just deliver the code?**

Delivering "just the code" is like giving someone a box of car engine parts with no assembly instructions, no driver's manual, and no key. The individual parts might be perfect, but the "product" is useless, dangerous, and impossible to fix.

The different components of the "Software Tree" are necessary to turn raw code into a complete, usable, and maintainable product:

- **Design Documents (Blueprints):** You need these to ensure you build the _right_ thing. Without a plan, you risk the components not fitting together, failing to meet user needs, and creating a system that's impossible to expand.
    
- **Source Code (The Recipe):** This is the core logic. You need it to fix bugs, add new features, or adapt the software for a new platform.
    
- **Executable (The Finished Cake):** This is the actual usable product for the end-user, who doesn't know or care about the source code.
    
- **System Manuals (User & Technical Guides):**
    
    - **User Manuals:** The software is useless if people don't know how to use it.
        
    - **Technical Manuals:** The software is unsupportable if IT staff don't know how to install, configure, or troubleshoot it.
        
- **Installation & Implementation:** The software provides no value if it's just sitting on a developer's hard drive. It must be installed on the user's system and integrated into their workflow.
    

In short, a software _product_ must deliver long-term value. This requires it to be **usable** (manuals), **functional** (executable), and **maintainable** (source code and design docs).

**3. Write a program to solve for the area and perimeter of a parallelogram and use it to differentiate between source code and executable.**

Here is a simple program in Visual Basic (as mentioned in the course notes). This code would be placed inside the "Click" event for a button on a form.

### Part A: The Program

This program assumes you have text boxes named `txtBase`, `txtHeight`, and `txtSide`, a button named `btnCalculate`, and labels named `lblArea` and `lblPerimeter`.

**This is the SOURCE CODE (saved in a `.vb` file):**

```
' This code runs when the user clicks the "btnCalculate" button
Private Sub btnCalculate_Click(sender As Object, e As EventArgs) Handles btnCalculate.Click
    
    ' 1. Get input from the user (from text boxes)
    ' We use Double to allow for decimal numbers
    Dim base As Double
    Dim height As Double
    Dim side As Double

    ' Use TryParse for safety, to avoid crashes if the user enters text
    Double.TryParse(txtBase.Text, base)
    Double.TryParse(txtHeight.Text, height)
    Double.TryParse(txtSide.Text, side)

    ' 2. Perform the calculations
    Dim area As Double = base * height
    Dim perimeter As Double = 2 * (base + side)

    ' 3. Display the output to the user (in labels)
    ' We use .ToString() to convert the number back to text
    lblArea.Text = "Area: " & area.ToString()
    lblPerimeter.Text = "Perimeter: " & perimeter.ToString()

End Sub
```

### Part B: Differentiating Source Code vs. Executable

- **Source Code:**
    
    - The VB code shown above is the **source code**.
        
    - It is a **human-readable** text file (`.vb`). You can open it in Notepad, read it, and understand its logic (e.g., `area = base * height`).
        
    - It is the "recipe." It _describes_ the program but is not the program itself.
        
    - You **cannot run** this file directly. Double-clicking a `.vb` file just opens it in a text editor.
        
- **Executable:**
    
    - After you "Build" or "Compile" this project in Visual Basic, it creates a new file, such as `ParallelogramSolver.exe`. This is the **executable**.
        
    - It is a **machine-readable** binary file. If you open it in Notepad, you will see unreadable symbols and gibberish.
        
    - It is the "finished cake." It is the actual, runnable application built _from_ the recipe.
        
    - This is the file you give to your users. They can **double-click the `.exe` file to run** your program and calculate the area of a parallelogram, even if they don't have Visual Basic installed.