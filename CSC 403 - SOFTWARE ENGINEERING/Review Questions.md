# 1. How to make an executable
Creating an executable (`.exe`) in Visual Basic 6.0 (VB6) is the process of compiling your source code into a standalone program.

Here is the step-by-step process.

### 1. Open Your Project

1. Launch **Microsoft Visual Basic 6.0**.
    
2. Click **File** > **Open Project** (or press `Ctrl+O`).
    
3. Browse to your project directory and select the project file (ending in `.vbp`).
    
4. Click **Open**.
    

### 2. Configure Project Properties (Recommended)

Before compiling, it is best practice to set your version numbers and compilation options.

1. Go to the **Project** menu and select **[YourProjectName] Properties...** (usually at the bottom of the list).
    
2. **General Tab:** Ensure the **Startup Object** is correct (e.g., `Form1` or `Sub Main`).
    
3. **Make Tab:**
    
    - **Version Number:** Update the Major, Minor, or Revision numbers.
        
    - **Icon:** Select the form that contains the icon you want to use for the `.exe` file.
        
    - **Version Information:** Enter details like "Company Name" or "Legal Copyright."
        
4. **Compile Tab:**
    
    - Select **Compile to Native Code**.
        
    - Choose **Optimize for Fast Code** (generally preferred for performance).
        
5. Click **OK** to save these settings.
    

### 3. Compile the Executable

1. Go to the **File** menu.
    
2. Select **Make [YourProjectName].exe...**.
    
3. A "Make Project" dialog box will appear.
    
    - **Save in:** Choose the folder where you want the `.exe` file to be created.
        
    - **File name:** Type the name you want for your application (e.g., `Calculator.exe`).
        
4. Click **OK**.
    

### 4. Verify Compilation

- **Progress:** You will see a compiling progress bar in the top right corner of the toolbar.
    
- **Errors:** If your code has syntax errors, the compiler will stop and highlight the line of code causing the issue. You must fix these errors and repeat Step 3.
    
- **Success:** If the progress bar finishes and disappears without errors, your executable is ready.
    

### 5. Test the Application

1. Navigate to the folder where you saved the file.
    
2. Double-click the new `.exe` file.
    
3. Ensure the program runs correctly without the VB6 IDE open.

# 2. How to create a package

# 3. Connecting VB to a API
Connecting to an API in Visual Basic 6 is typically done using the **Microsoft XML, v6.0** library. This allows you to perform HTTP requests (GET, POST, etc.) similar to how modern languages use `fetch`.

Here is the step-by-step guide.

### 1. Add the Reference

You must enable the library that handles HTTP requests.

1. Open your VB6 Project.
    
2. Go to **Project** > **References**.
    
3. Scroll down and check **Microsoft XML, v6.0** (if 6.0 is missing, v4.0 or v3.0 usually work as well).
    
4. Click **OK**.
    

### 2. The Code (GET Request)

Use the `MSXML2.XMLHTTP` object to fetch data. Here is a complete subroutine you can copy into your form.

VB.Net

```
Private Sub CallAPI()
    ' 1. Declare the object
    Dim http As New MSXML2.XMLHTTP60
    Dim url As String
    Dim responseText As String

    ' 2. Define the endpoint
    url = "https://jsonplaceholder.typicode.com/posts/1"

    ' 3. Initialize the Request
    ' Syntax: .Open(Method, URL, Async)
    ' False = Wait for response (Synchronous). Freezes UI briefly.
    http.Open "GET", url, False

    ' 4. Add Headers (Required by most modern APIs)
    http.setRequestHeader "Content-Type", "application/json"
    http.setRequestHeader "User-Agent", "VB6-Client"

    ' 5. Send the Request
    On Error GoTo ErrorHandler
    http.send

    ' 6. Check the Status (200 means OK)
    If http.Status = 200 Then
        responseText = http.responseText
        ' Output the raw JSON string
        MsgBox "Success: " & vbCrLf & responseText
    Else
        MsgBox "Error " & http.Status & ": " & http.statusText
    End If

    Exit Sub

ErrorHandler:
    MsgBox "Connection Failed: " & Err.Description
End Sub
```

### 3. The Code (POST Request)

If you need to send data _to_ the server (e.g., a login form), use `POST` and pass the data in the `.send` method.

VB.Net

```
Private Sub PostToAPI()
    Dim http As New MSXML2.XMLHTTP60
    Dim url As String
    Dim jsonBody As String
    
    url = "https://jsonplaceholder.typicode.com/posts"
    
    ' Construct JSON manually (VB6 has no native JSON builder)
    jsonBody = "{""title"":""My Post"",""body"":""Hello World"",""userId"":1}"
    
    http.Open "POST", url, False
    http.setRequestHeader "Content-Type", "application/json"
    
    ' Send the body data
    http.send jsonBody
    
    MsgBox "Server Reply: " & http.responseText
End Sub
```

### 4. Handling JSON Responses

VB6 does not have a native JSON parser. When you receive `http.responseText`, it is just a long string. To read specific values (like extracting an ID or Name), you have three options:

1. **String Parsing:** Use `InStr`, `Mid`, and `Split` to hack out the text you need (Messy, but no dependencies).
    
2. **MSScriptControl:** Use the "Microsoft Script Control" reference to run JavaScript `eval()` on the string (Quick and effective).
    
3. **Third-Party Class:** Add a library like `VB-JSON` to your project (Best for complex data).
    

### 5. Important Warning on TLS/SSL

Modern APIs require **TLS 1.2** security.

- If you run your VB6 app on **Windows 10/11**, the OS handles this automatically, and it should work.
    
- If you run this on **Windows XP/7**, the connection will likely fail because the OS does not support the security protocols used by modern APIs.

# 4. Methodologies
### (i) Waterfall Model

This is the oldest and most traditional method. It is a linear, sequential approach where the development flows downwards (like a waterfall) through distinct phases.

- **How it works:** You must complete one phase entirely before moving to the next. You generally cannot go back to a previous phase without restarting.
    
- **Phases:** Requirements $\rightarrow$ Design $\rightarrow$ Implementation $\rightarrow$ Testing $\rightarrow$ Deployment $\rightarrow$ Maintenance.
    
- **Best for:** Projects with very clear, fixed requirements that won't change (e.g., military or medical software).
    

![Image of waterfall model software development diagram](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcTdf9sO6_tb0weION3_t_QBvWNLV407ZXt4XAaGwhHf-SGSDyCrn9OOYNwZqjLfV33V_XdodToEC_H5vV4ZTS8x0mzwI7pQXctVx-7eTMN_mgkAFsI)

Shutterstock

Explore

### (ii) Prototyping Technique

This method focuses on creating an early, working model (a prototype) of the software to show the user before building the real thing.

- **How it works:** The developer builds a quick, "rough draft" version of the interface. The user plays with it and gives feedback. The developer refines it or throws it away and builds the real system based on that feedback.
    
- **Best for:** Projects where the users don't know exactly what they want yet. It reduces the risk of building the wrong product.
    

### (iii) Iterative and Incremental Development

This approach breaks the project down into smaller chunks rather than trying to build the whole thing at once.

- **Incremental:** You build the software piece by piece. (e.g., First build the Login screen, then build the Reporting screen, then build the Printing screen).
    
- **Iterative:** You build a rough version of the whole system, and then repeatedly refine it to make it better (e.g., Version 1.0, Version 1.1, Version 2.0).
    
- **Best for:** Large projects where you need to get a basic version to the market quickly and improve it later.
    

![Image of iterative and incremental development diagram](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcRF63REaqsE4n-hCapWwax8TCZqr9yymuDFok4isoCH-u_v2xZ4awGpePewc81MAn538fyVRwetu7eUgDIypcohCxztYeHH6avKUVf51hdJhQcS14g)

Shutterstock

Explore

### (iv) Spiral Method / Development

The Spiral model combines elements of the Waterfall model with Prototyping, but its primary focus is on **Risk Analysis**.

- **How it works:** The project moves in a spiral. In every loop (iteration), the team analyzes risks (what could go wrong?), builds a prototype to test that risk, and then plans the next loop.
    
- **Key Feature:** It is the only model that explicitly prioritizes risk management at every stage.
    
- **Best for:** Very large, expensive, and high-risk projects (e.g., NASA software).
    

![Image of spiral model software development diagram](https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcSXN3jOCKbBB67HXsYlC6-yvzEEIy6ZxvheJ0M7bXhfD68I2OZfAqnSJlAxiuYoCrufuYKolj3SCvrgu4fYbVOQdsaN9hkT2c5qH1uWpjiC6xryLHk)

Shutterstock

Explore

### (v) Rapid Application Development (RAD)

RAD focuses on speed and user feedback rather than strict planning. It emphasizes using tools (like Visual Basic 6!) to quickly drag-and-drop interfaces.

- **How it works:** It uses "Time Boxing" (strict deadlines) and heavy user involvement. Developers use pre-built components to assemble apps quickly.
    
- **Best for:** Projects that need to be done very fast (e.g., 2-3 months) and have a highly available user to test things daily.
    

### (vi) Extreme Programming (XP)

XP is a type of **Agile** development that focuses on technical excellence and responsiveness to changing customer requirements.

- **How it works:** It uses specific engineering practices to ensure quality.
    
    - **Pair Programming:** Two developers share one computer (one types, one reviews).
        
    - **Test-Driven Development (TDD):** Writing the test _before_ writing the code.
        
    - **Small Releases:** Releasing updates very frequently.
        
- **Best for:** Projects where requirements change constantly and high code quality is critical.
    

### (vii) Parallel Technique

This usually refers to **Parallel Development**, where a project is split into distinct sub-projects that are developed simultaneously by different teams.

- **How it works:** Instead of one team doing A then B then C, Team 1 does A, Team 2 does B, and Team 3 does C at the same time. They integrate everything at the end.
    
- **Best for:** Projects with a tight deadline that have independent modules which can be built separately without interfering with each other.
    

> **Note:** In some contexts (System Implementation), "Parallel" can refer to running the old system and the new system at the same time to ensure the new one works. However, in the context of this list, it likely refers to the development strategy described above.

# 5. Connect VB to an API
The standard method for connecting VB6 to a database is using **ADO (ActiveX Data Objects)**.

Here is the complete guide and code to Connect, Read, Insert, Update, and Delete.

### Step 1: Add the Reference

You cannot run the code without this step.

1. Open your VB6 project.
    
2. Go to **Project** > **References**.
    
3. Scroll down and check **Microsoft ActiveX Data Objects 2.8 Library** (or 6.1, whichever is highest).
    
4. Click **OK**.
    

### Step 2: The Setup

This example assumes you are connecting to a standard **Microsoft Access Database (`.mdb`)**.

**Scenario:** We have a table named `Users` with two columns:

- `UserID` (Number/AutoNumber)
    
- `Username` (Text)
    

### Step 3: The Code

Copy this code into your Form.

VB.Net

```
Option Explicit

' Declare the Connection and Recordset objects globally
Dim conn As ADODB.Connection
Dim rs As ADODB.Recordset
Dim dbPath As String

' 1. CONNECT TO DATABASE
Private Sub Form_Load()
    ' Define the path to your database file
    dbPath = App.Path & "\MyDatabase.mdb"
    
    Set conn = New ADODB.Connection
    
    ' Connection String for Access 2000-2003 (.mdb)
    ' If using Access 2007+ (.accdb), change Provider to Microsoft.ACE.OLEDB.12.0
    conn.ConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=" & dbPath
    
    ' Open the connection
    On Error GoTo ConnError
    conn.Open
    MsgBox "Connected successfully!"
    Exit Sub

ConnError:
    MsgBox "Connection Failed: " & Err.Description
End Sub

' 2. READ DATA (SELECT)
Private Sub btnRead_Click()
    Set rs = New ADODB.Recordset
    
    ' Open the recordset (Table, Connection, CursorType, LockType)
    rs.Open "SELECT * FROM Users", conn, adOpenStatic, adLockReadOnly
    
    ' Loop through the data
    If Not rs.EOF Then
        rs.MoveFirst
        Do Until rs.EOF
            Debug.Print "ID: " & rs!UserID & " - Name: " & rs!Username
            rs.MoveNext
        Loop
        MsgBox "Data printed to Immediate Window (Ctrl+G)"
    Else
        MsgBox "No records found."
    End If
    
    ' Always close the recordset when done
    rs.Close
End Sub

' 3. INSERT DATA
Private Sub btnAdd_Click()
    Dim sql As String
    Dim newName As String
    newName = "JohnDoe"
    
    ' It is cleaner to use SQL Execution for Insert/Update/Delete
    sql = "INSERT INTO Users (Username) VALUES ('" & newName & "')"
    
    On Error GoTo WriteError
    conn.Execute sql
    MsgBox "User Added!"
    Exit Sub

WriteError:
    MsgBox "Error adding user: " & Err.Description
End Sub

' 4. UPDATE DATA
Private Sub btnUpdate_Click()
    Dim sql As String
    ' Change User with ID 1 to verify the name
    sql = "UPDATE Users SET Username = 'JaneDoe' WHERE UserID = 1"
    
    conn.Execute sql
    MsgBox "User Updated!"
End Sub

' 5. DELETE DATA
Private Sub btnDelete_Click()
    Dim sql As String
    ' Delete User with ID 1
    sql = "DELETE FROM Users WHERE UserID = 1"
    
    conn.Execute sql
    MsgBox "User Deleted!"
End Sub

' 6. CLEAN UP (Important!)
Private Sub Form_Unload(Cancel As Integer)
    ' Close the connection when the app closes to free memory
    If conn.State = adStateOpen Then conn.Close
    Set conn = Nothing
    Set rs = Nothing
End Sub
```

### Summary of Key Commands

|Action|VB6/ADO Method|
|---|---|
|**Connect**|`conn.Open "ConnectionString"`|
|**Read**|`rs.Open "SELECT..."` then loop with `rs.MoveNext`|
|**Write**|`conn.Execute "INSERT INTO..."`|
|**Modify**|`conn.Execute "UPDATE..."`|
|**Remove**|`conn.Execute "DELETE..."`|

Export to Sheets

### Important Note on Security

The code above creates SQL strings directly (e.g., `'VALUES ('" & newName & "')'`). In a real application, if `newName` comes from a user typing into a textbox, this is vulnerable to **SQL Injection** hacking.

For a student project, the code above is fine. For a professional app, you would need to use `ADODB.Command` and **Parameters** to scrub the input safely.

# 6. How to deploy applications
Deployment implies taking your compiled code and moving it to a place where users can actually use it. The process is completely different for each platform.

Here is a breakdown of how deployment works for Web, Mobile, Desktop, and Embedded systems.

---

### 1. Web Application Deployment

Web apps live on servers, not on the user's device. Deployment means updating that server.

- **The Concept:** You push your code to a remote computer (Server/Cloud) which processes requests from users' browsers.
    
- **Modern Method (CI/CD):**
    
    1. **Push Code:** You save your code to a repository (like GitHub).
        
    2. **Build:** An automated tool (like Jenkins or GitHub Actions) compiles the code and runs tests.
        
    3. **Deploy:** The tool automatically copies the files to the server or cloud provider (AWS, Azure, Vercel).
        
- **Traditional Method (FTP):** You manually use software like FileZilla to drag and drop files from your computer to the server.
    
- **Key Tools:**
    
    - **Frontend:** Vercel, Netlify (Drag and drop deployment).
        
    - **Backend:** AWS EC2, Heroku, Docker (Containerization).
        

### 2. Mobile Application Deployment

Mobile apps live on the user's phone, but you cannot send files directly to them. You must go through "Walled Gardens" (App Stores).

- **The Concept:** You submit your binary file to Apple or Google. They review it for safety and policy violations. Once approved, they release it to users.
    
- **The Steps:**
    
    1. **Code Signing:** You must digitally sign your app with a certificate (costing money) to prove you are the developer.
        
    2. **Build:** Create an `.apk` / `.aab` (Android) or `.ipa` (iOS) file.
        
    3. **Submission:** Upload the file to **Google Play Console** or **Apple App Store Connect**.
        
    4. **Review:** Wait 1–3 days for the company to approve your app.
        
    5. **Release:** Users get a notification to download or update.
        
- **Key Difficulty:** Apple is very strict. If your app crashes or breaks a rule, they will reject the deployment.
    

### 3. Desktop Application Deployment

Desktop deployment is about getting an installer file (`setup.exe` or `.dmg`) onto the user's machine.

- **The Concept:** You bundle your code and dependencies into a single package that the user downloads and runs.
    
- **Method A: Direct Download (Traditional)**
    
    1. **Package:** Use a tool (like Inno Setup for VB6, or WiX for modern apps) to create an installer.
        
    2. **Host:** Upload the installer to your website.
        
    3. **Update:** Your app must have a built-in "Check for Updates" feature to download new versions, otherwise users stay on the old version forever.
        
- **Method B: Store Deployment (Modern)**
    
    - Submit your app to the **Microsoft Store** or **Mac App Store**. The Store handles auto-updates and installation automatically (similar to mobile).
        

### 4. Embedded Systems Deployment

Embedded deployment (IoT) involves putting code onto hardware chips (Microcontrollers like Arduino, ESP32, or STM32).

- **The Concept:** The code is "flashed" directly into the permanent memory of the device.
    
- **Method A: Physical Flashing (Factory/Dev)**
    
    - You connect the hardware to a PC via USB or a JTAG debugger.
        
    - A programmer tool writes the binary (hex file) to the chip.
        
- **Method B: OTA (Over-the-Air)**
    
    - Modern IoT devices (like Smart Bulbs) connect to Wi-Fi.
        
    - The device checks a server for a new firmware version.
        
    - It downloads the new code to a temporary memory slot, verifies it, and then reboots into the new version.
        
- **Key Risk:** If embedded deployment fails (e.g., power cuts during update), the device can become "bricked" (permanently broken).

# 7. Difference between package and program
In Visual Basic 6, the difference between an **Application Program** and an **Application Package** is the difference between the "app itself" and the "installer kit" needed to put that app on another computer.

Here is the breakdown of the differences.

### 1. The Definitions

- **Application Program (The Executable)** This is the actual software you built. In VB6, this is the single `.exe` file (e.g., `Calculator.exe`) created when you click **File > Make...**. It contains your compiled code and forms.
    
- **Application Package (The Installer)** This is a collection of files bundled together to help users install your program. In VB6, this is created by the **Package & Deployment Wizard**. It includes your `.exe`, but also adds the installer (`setup.exe`) and all the hidden system files your app needs to run.
    

### 2. Detailed Comparison

|Feature|Application Program|Application Package|
|---|---|---|
|**Main File**|Just the `.exe` file.|A folder containing `Setup.exe`, `Setup.lst`, and `.CAB` files.|
|**Purpose**|To **run** the specific task (e.g., calculate numbers).|To **install** the software onto a computer.|
|**Dependencies**|Does **not** include the required DLLs or OCXs inside it.|**Includes** all necessary DLLs, OCXs, and VB6 Runtimes.|
|**Portability**|Usually **fails** if copied to a new computer (missing DLL errors).|**Works** on new computers because it installs what is missing.|
|**How to Create**|VB6 Menu: **File > Make Project.exe**|Add-In: **Package & Deployment Wizard**|

Export to Sheets

### 3. Why the "Package" is Necessary (The DLL Issue)

New VB6 developers often make the mistake of just copying the **Application Program** (`Project1.exe`) to a friend's computer.

- **The Problem:** When the friend tries to run it, they get an error: _"Component 'MSCOMCTL.OCX' or one of its dependencies not correctly registered."_ This happens because VB6 apps are not standalone; they rely on system files that might be missing on the friend's PC.
    
- **The Solution:** The **Application Package** solves this. The `setup.exe` inside the package checks the friend's computer for missing files, installs them, registers them, and _then_ copies your program.
    

### Summary

- **Application Program:** The engine (The code you wrote).
    
- **Application Package:** The shipping container (The engine + the tools needed to install it)