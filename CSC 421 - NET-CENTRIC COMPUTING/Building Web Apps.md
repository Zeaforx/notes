# 🎓 Student Note: Building Web Applications

**Module: NetCentric Lecture CSC 421**

## INTRODUCTION

**What is a Web Application?**

A web app is an interactive computer program built with web technologies (HTML, CSS, JS) that stores data (in a database) and allows users to manipulate that data (CRUD - Create, Read, Update, Delete).

> **💡 Student Note (Analogy):**
> 
> Think of a **Website** (like a news site) as a digital brochure—you just read it.
> 
> Think of a **Web App** (like Gmail or Facebook) as a digital tool—you log in, create content, delete items, and interact with it.

**Core Components:**

1. **Front-end (Client-side):** What users see. Built with HTML (structure), CSS (style), and JavaScript (interactivity).
    
2. **Back-end (Server-side):** The logic and data storage. Built with languages like Python, PHP, or Node.js.
    

## 3.0 MAIN CONTENT

### 3.1 Prerequisites for Building a Web Application

To build a data-centric app from scratch, you generally need to understand three layers:

1. **Backend Language:** (e.g., Python, Ruby) - Controls _how_ the app functions.
    
2. **Web Front End:** (HTML, CSS, Javascript) - Controls the _look and feel_.
    
3. **DevOps:** (GitHub, Jenkins) - Handles _deploying_ (putting it on the internet) and hosting.
    

_Don't know these? You have two options:_

- **Option 1:** Learn them (Codecademy is a good resource).
    
- **Option 2:** Use a **Web App Builder** (like Budibase). These "Low-Code" tools handle the complex coding and hosting for you.
    

### 3.2 STEPS TO BUILDING A WEB APPLICATION

#### 3.2.1 Step 1: Source an Idea

Before writing code, you need a purpose. The best ideas solve a problem—ideally, one _you_ have.

- _Ask yourself:_ What apps do I enjoy? How will this app save time or money?
    

#### 3.2.2 Step 2: Market Research

Verify if people actually want your idea.

- **Product-Market Fit:** Being in a good market with a product that satisfies that market.
    
- **Tools to check if it exists:** Google, Product Hunt, BetaList.
    
- _Scenario A (It exists):_ Good! That means there is a market. You just need to do it better.
    
- _Scenario B (It doesn't exist):_ You might be a genius, or there might be no demand. Investigate further using Google Trends or SEO tools (checking search volume for keywords).
    

#### 3.2.3 Step 3: Define Functionality

List exactly what your app will do. **Keep it simple** for Version 1.

- _Example (CRM App Features):_ Users can create accounts, reset passwords, create contacts, and label contacts (Lead/Customer).
    

#### 3.2.4 Step 4: Sketch Your Web App

Use a pen and paper. Sketch the user interface (UI).

- Focus on navigation, buttons, and forms.
    
- Don't worry about making it pretty yet; worry about how it _works_.
    

#### 3.2.5 Step 5: Plan Workflow

Map out the user's journey.

- _Analyze Competitors:_ Sign up for their free trials. What is their login process like? How do they handle payments?
    
- _Map Your Flow:_ How does a user go from "Sign Up" -> "Dashboard" -> "Logout"? Note that a "Logged In" user sees different pages than a "Logged Out" user.
    

#### 3.2.6 Step 6: Wireframing / Prototyping

Turn sketches into a digital blueprint.

- **Wireframe:** A static blueprint (like a floor plan).
    
- **Prototype:** An interactive model (clickable buttons).
    
- _Tools:_ Figma, Adobe XD, Balsamiq.
    

#### 3.2.7 Step 7: Seek Early Validation

Show your prototype to potential users (not just friends).

- Go to forums or events where your target audience hangs out.
    
- **Goal:** Get constructive criticism. Ideally, get pre-launch sales or sign-ups.
    

#### 3.2.8 Before Development: "The MEP Strategy"

**MEP (Minimal Excellent Product):**

- Build a **"Complete Vertical"**: Get one small feature fully working from front-end to database, rather than half-building everything.
    
- _Advice:_ Expect things to change. Don't be afraid to delete code. Learn your tools properly.
    

#### 3.2.9 Step 8: Architect and Build Your Database

**What is a Database?**

A collection of data. A DBMS (Database Management System) allows you to Create, Read, Update, and Delete that data securely.

**Type A: SQL (Relational)**

- _Best for:_ Data with strict relationships (e.g., An "Invoice" must belong to a "Customer").
    
- _Structure:_ Tables with rows and columns.
    
- _Examples:_ MySQL, PostgreSQL, SQL Server.
    
- _Pros:_ Powerful queries, reliable.
    
- _Cons:_ You must define the structure (schema) upfront. Harder to change later.
    

**Type B: Document Database (NoSQL)**

- _Best for:_ Flexible data that might change shape.
    
- _Structure:_ "Documents" (often JSON files) stored in a collection.
    
- _Examples:_ MongoDB, Firebase, DynamoDB.
    
- _Pros:_ Flexible (schemaless), easier to scale.
    
- _Cons:_ Complex relationships (joins) are harder to manage manually.
    

**Data Segregation (Keeping Client Data Safe):**

1. **Physical Separation:** Every client gets their own separate database.
    
    - _Pros:_ Most secure. If one DB breaks, others are safe.
        
    - _Cons:_ Hard to manage and upgrade.
        
2. **Logical Separation:** All clients share one giant database, but every query has a filter (e.g., `WHERE ClientID = 123`).
    
    - _Pros:_ Easy to manage and query.
        
    - _Cons:_ High risk. One missing filter in your code could leak data to the wrong user.
        

#### 3.2.10 Step 9: Build the Frontend

This is the visual part (HTML/CSS/JS).

**Development Environment:**

- **Code Editor:** VS Code.
    
- **Package Manager:** Webpack (bundles your code).
    
- **Frameworks:** React, Vue, Svelte (Recommended for modern apps).
    

**Single Page Application (SPA):**

- The app loads once, and clicking links just updates the content instantly without refreshing the page (like an app).
    
- _Note:_ Requires setting up a "proxy" during development so the frontend server can talk to the backend server.
    

#### 3.2.11 Step 10: Build the Backend

The "Brain" of the application.

**Key Responsibilities:**

1. **Endpoints:** Providing API URLs (e.g., `/api/get-users`) for the frontend to call.
    
2. **Authentication:** verifying _who_ the user is (Login).
    
3. **Authorization:** Verifying _what_ the user is allowed to do (Permissions).
    

**Choosing a Framework:**

- If you know Python: Use **Django** or **Flask**.
    
- If you know JavaScript: Use **Express (Node.js)**.
    
- If you want a shortcut: Use **Budibase**.
    

#### 3.2.12 Step 11: Host Your Web Application

Where does the app live on the internet?

- **Cloud Providers:** Amazon AWS, Google Cloud, Azure (Powerful but complex).
    
- **PaaS (Platform as a Service):** Heroku, Firebase, Digital Ocean (Easier, often cheaper for small apps).
    
- **Essentials:** You need a Domain Name (Namecheap) and an SSL Certificate (security).
    

#### 3.2.13 Step 12: Deploy Your Web App

Moving code from your laptop to the server.

- **Tools:** Git (Source Control), Jenkins, GitLab CI.
    
- **CI/CD:** Continuous Integration/Deployment. Automating the process so when you save code, it automatically updates the live website.
    

## 5.0 & 6.0 CONCLUSION AND SUMMARY

Building a web app is a journey from **Ideation** -> **Validation** -> **Design** -> **Development** -> **Deployment**.

- **Front-end:** Look and Feel (HTML/CSS/React).
    
- **Back-end:** Logic and Data Management (Python/Node).
    
- **Database:** SQL (Structured) vs NoSQL (Flexible).
    
- **Security:** Crucial, especially regarding how you separate different users' data in the database.
    

**Practical Tips:**

- Start small (MEP).
    
- Validate before you build.
    
- Don't be afraid to use tools (like Budibase) to speed up the process.