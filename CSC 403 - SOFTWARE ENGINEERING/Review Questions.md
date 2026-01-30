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

# 3. Connecting VB to a db
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