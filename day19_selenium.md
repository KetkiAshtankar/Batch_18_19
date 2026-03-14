# 1. What is PyCharm?

### Definition

**PyCharm is an Integrated Development Environment (IDE) used to write, run, debug, and manage Python programs.**

It provides tools that make coding faster and easier.

---

# IDE vs Code Editor

| Feature    | IDE                                      | 
| ---------- | ---------------------------------------- | 
| Definition | Complete development environment         | 
| Tools      | Debugger, testing tools, package manager | 
| Example    | PyCharm                                  | 

---

# Features of PyCharm

### 1. IntelliSense (Auto-completion)

Suggests code automatically while typing.

Example:

```python
driver.find_element
```

---

### 2. Debugger

Helps find errors by executing code step-by-step.

You can:

* Pause execution
* Check variable values
* Identify bugs easily

---

### 3. Git Integration

Supports version control systems such as:

* Git
* GitHub

Helps teams collaborate on code.

---

### 4. Testing Tools

Supports testing frameworks like:

* Pytest
* Unittest

Useful for automation testing.

---

### 5. Virtual Environment Support

PyCharm automatically manages **virtual environments** for each project.

---

# PyCharm Versions

| Version      | Description  |
| ------------ | ------------ |
| Community    | Free version |
| Professional | Paid version |

Most automation projects use **Community Edition**.

---

# 2. What is a Python Virtual Environment?

### Definition

A **virtual environment** is an isolated Python environment that allows each project to have its own dependencies and packages.

---

# Why Virtual Environment is Important

### 1. Avoid Version Conflicts

Example:

Project A requires:

```
selenium 4.0
```

Project B requires:

```
selenium 3.14
```

Without virtual environment → conflict occurs.

With virtual environment → both projects work independently.

---

### 2. Project Isolation

Each project maintains its own:

* Python packages
* Libraries
* Dependencies

---

### 3. Clean Dependency Management

Only required libraries are installed.

Example packages:

```
selenium
pytest
webdriver-manager
```

---

# Typical Project Structure

```
ProjectFolder
│
├── venv
│   ├── Scripts
│   ├── Lib
│   └── Include
│
├── test_script.py
└── requirements.txt
```

---

# Creating a Virtual Environment

Command:

```bash
python -m venv venv
```

This creates a folder named **venv**.

---

# Activating Virtual Environment

### Windows PowerShell

```powershell
.\venv\Scripts\Activate.ps1
```

### Windows CMD

```bash
venv\Scripts\activate.bat
```

### Mac / Linux

```bash
source venv/bin/activate
```

When activated, terminal shows:

```
(venv)
```

---

# Installing Selenium

After activating the environment, install Selenium using pip.

```bash
pip install selenium
```

This installs:

Selenium WebDriver

---

# Verify Installation

Check installed packages:

```bash
pip list
```

or

```bash
pip show selenium
```

Example output:

```
selenium 4.x.x
```

---

# Upgrading Selenium

To install the latest version run:

```bash
pip install --upgrade selenium
```

Then verify:

```bash
pip show selenium
```

---

# Example Selenium Script

```python
from selenium import webdriver

driver = webdriver.Chrome()

driver.get("https://www.google.com")

print(driver.title)

driver.quit()
```

What this script does:

1. Opens Chrome browser
2. Navigates to Google
3. Prints page title
4. Closes the browser

---

# Common Errors and Fixes

## 1. Virtual Environment Not Found

Error:

```
ObjectNotFound: venv\Scripts\activate.ps1
```

Solution:

Create environment:

```bash
python -m venv venv
```

---
---

# Selenium Architecture

Selenium WebDriver

### Definition

Selenium Architecture explains **how Selenium commands travel from the test script to the browser and execute actions**.

It describes the **communication between the test script, WebDriver, browser drivers, and browser**.

---

# Components of Selenium Architecture

The architecture mainly consists of:

1. Test Script
2. Client Libraries (Language Bindings)
3. WebDriver Protocol
4. Browser Drivers
5. Browser

---

# 1. Test Script

Testers write automation scripts in programming languages such as:

* Python
* Java
* C#
* JavaScript

Example:

```python
from selenium import webdriver
driver = webdriver.Chrome()
driver.get("https://google.com")
```

This script tells Selenium to **open Chrome and navigate to Google**.

---

# 2. Client Libraries (Language Bindings)

Client libraries act as **a bridge between the test script and WebDriver**.

They convert commands written in programming languages into **HTTP requests**.

Example:

Python code

```python
driver.find_element()
```

is converted into **WebDriver commands**.

---

# 3. WebDriver Protocol

The protocol defines **how commands are sent to the browser driver**.

Two protocols have been used:

### JSON Wire Protocol (Selenium 3)

Used in Selenium 3 to communicate with browsers.

Commands are sent in **JSON format using HTTP requests**.

Example request:

```
POST /session
{
"browserName": "chrome"
}
```

---

### W3C WebDriver Protocol (Selenium 4)

Selenium 4 uses the **official WebDriver standard** defined by:

World Wide Web Consortium

Advantages:

* Standard communication across browsers
* Faster execution
* Better stability
* No compatibility issues

---

# 4. Browser Drivers

Browser drivers act as **a translator between Selenium and the browser**.

Examples:

* ChromeDriver
* GeckoDriver
* EdgeDriver

Role of driver:

* Receives commands from Selenium
* Interacts with the browser
* Sends response back to the script

---

# 5. Browser

The browser performs the actual actions such as:

* Opening a webpage
* Clicking buttons
* Entering text
* Submitting forms

Supported browsers include:

* Chrome
* Firefox
* Edge
* Safari

---

# Communication Flow (Execution Flow)

```
Test Script
     ↓
Client Library
     ↓
WebDriver Protocol
     ↓
Browser Driver
     ↓
Browser
```

Example Flow:

1. Script sends command: `driver.get()`
2. Client library converts command into HTTP request
3. Request is sent to browser driver
4. Driver instructs browser to perform action
5. Browser executes action and sends response back

---

# Selenium 3 vs Selenium 4

| Feature               | Selenium 3          | Selenium 4                  |
| --------------------- | ------------------- | --------------------------- |
| Protocol              | JSON Wire Protocol  | W3C WebDriver Protocol      |
| Browser Communication | Indirect            | Standardized                |
| Driver Management     | Manual driver setup | Automatic driver management |
| New Features          | Limited             | Many new features           |
| Stability             | Less stable         | More stable                 |
| Grid                  | Complex setup       | Simplified architecture     |

---

# New Features in Selenium 4

1. **W3C Standard Protocol**

Ensures consistent communication with browsers.

---

2. **Relative Locators**

Allows locating elements relative to other elements.

Example:

```python
from selenium.webdriver.support.relative_locator import locate_with
```

---

3. **Improved Selenium Grid**

Better UI and easier setup.

---

4. **Better Window and Tab Management**

New methods to switch windows.

---

# Types of Selenium

Selenium is not a single tool. It is a **suite of tools**.

The main components are:

1. Selenium IDE
2. Selenium WebDriver
3. Selenium Grid

---

# 1. Selenium IDE

Selenium IDE

### Definition

Selenium IDE is a **browser extension used to record and playback test cases**.

It allows testers to **create tests without writing code**.

---

### Features

* Record browser actions
* Playback tests
* Export scripts

---

### Advantages

* Easy to learn
* No programming required
* Good for beginners

---

### Limitations

* Limited functionality
* Not suitable for complex automation
* Limited browser support

---

# 2. Selenium WebDriver

Selenium WebDriver

### Definition

Selenium WebDriver is an **automation tool used to interact with web browsers programmatically**.

Testers write scripts to automate browser actions.

---

### Features

* Supports multiple programming languages
* Supports multiple browsers
* Allows complex automation

---

### Example

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com")
```

---

### Advantages

* Highly flexible
* Supports frameworks
* Used in real industry projects

---

# 3. Selenium Grid

Selenium Grid

### Definition

Selenium Grid allows tests to run on **multiple machines and browsers simultaneously**.

This helps in **parallel execution**.

---

### Architecture

```
Test Script
      ↓
     Hub
   /   |   \
 Node Node Node
```

* **Hub** → Central controller
* **Nodes** → Machines running tests

---

### Advantages

* Faster test execution
* Cross-browser testing
* Distributed testing

---

# Comparison of Selenium Components

| Feature   | Selenium IDE   | Selenium WebDriver | Selenium Grid           |
| --------- | -------------- | ------------------ | ----------------------- |
| Purpose   | Record tests   | Automate browsers  | Run tests in parallel   |
| Coding    | Not required   | Required           | Required                |
| Usage     | Beginners      | Automation testers | Large test environments |
| Execution | Single browser | Single machine     | Multiple machines       |

---
