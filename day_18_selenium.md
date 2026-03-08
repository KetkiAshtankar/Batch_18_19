
---

# Selenium Automation – Session Notes

## 1. What is Automation Testing?

Automation Testing means **using software tools and scripts to automatically test applications instead of testing manually**.

### Example

Manual testing steps:

1. Open browser
2. Go to website
3. Enter username
4. Enter password
5. Click login
6. Verify login success

If this has to be done **100 times**, it becomes repetitive.

Automation testing allows a **program to perform these steps automatically**.

### Analogy

Manual testing → Washing clothes by hand
Automation testing → Washing machine

Both achieve the same result, but automation **saves time and effort**.

---

# 2. What is Selenium?

Selenium is an **open-source automation tool used to test web applications by controlling browsers automatically**.

It allows testers to write scripts that can:

* Open browsers
* Click buttons
* Enter text
* Navigate pages
* Validate results

### Example

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://www.google.com")
```

This script automatically opens Google in the browser.

---

# 3. Selenium Architecture (How it Works)

Automation flow:

```
Test Script → Selenium → ChromeDriver → Browser
```

Components:

1. **Test Script** – Code written by tester
2. **Selenium WebDriver** – API to control browsers
3. **Browser Driver** – Communicates with browser
4. **Browser** – Chrome / Firefox / Edge

Example driver:

ChromeDriver allows Selenium to control
Google Chrome.

---

# 4. What is a Selenium Framework?

A **framework** is a **structured way to organize automation code**.

It provides:

* Folder structure
* Reusable functions
* Test data management
* Reporting
* Logging

### Example Framework Structure

```
project
│
├── tests
├── pages
├── utilities
├── reports
└── data
```

### Analogy

Ingredient = Selenium
Recipe + Kitchen Setup = Framework

Without framework → messy code
With framework → organized and maintainable tests.

---

# 5. Why Selenium is Popular (Advantages)

### 1. Open Source

Free to use.

### 2. Supports Multiple Languages

* Python
* Java
* JavaScript
* C#
* Ruby

### 3. Supports Multiple Browsers

* Chrome
* Firefox
* Edge
* Safari

### 4. Supports Multiple Operating Systems

* Windows
* Mac
* Linux

### 5. Large Community Support

Huge developer and tester community.

### 6. Tool Integration

Works with tools like:

* Jenkins
* pytest
* CI/CD pipelines

---

# 6. Selenium Versions

### Selenium 1 (Selenium RC)

Old architecture.

Limitations:

* Slow execution
* Complex setup

Not used today.

---

### Selenium 2 (WebDriver)

Introduced **WebDriver**.

Advantages:

* Direct browser communication
* Faster and more stable

---

### Selenium 3

* Improved stability
* Removed Selenium RC

---

### Selenium 4 (Current Version)

Major improvements:

* Built-in driver management
* DevTools integration
* Better Selenium Grid
* Improved browser support

---

# 7. Supported Platforms

### Operating Systems

* Windows
* Mac
* Linux

### Browsers

* Chrome
* Firefox
* Edge
* Safari

### Programming Languages

* Python
* Java
* JavaScript
* C#
* Ruby

---

# 8. Functional Testing vs Performance Testing

### Functional Testing

Checks **whether the application works correctly**.

Example:

* Login functionality
* Button click
* Form submission

This is what Selenium does.

---

### Performance Testing

Checks **system speed and stability under load**.

Example questions:

* How many users can access the system?
* How fast does the server respond?

Tools used for performance testing:

* Apache JMeter
* LoadRunner
* k6

Selenium is **not suitable for performance testing** because it opens real browsers.

---

# 9. Installing Selenium

Install Selenium using pip:

```bash
pip install selenium
```

If pip command fails:

```bash
python -m pip install selenium
```

Verify installation:

```bash
pip show selenium
```

---

# 10. Simple Selenium Script

Example:

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://www.google.com")
```

What happens:

1. Selenium starts Chrome
2. Browser opens automatically
3. Google website loads

---

# 11. ChromeDriver Version Error

Common error:

```
This version of ChromeDriver only supports Chrome version 141
Current browser version is 145
```

Meaning:

ChromeDriver version and Chrome browser version do not match.

Example:

ChromeDriver → 141
Chrome Browser → 145

Solution:

* Use matching driver
* Or use Selenium automatic driver management.

---

# 12. Selenium 4 Automatic Driver Management

From Selenium 4.6 onwards, driver download is automatic.

Example:

```python
from selenium import webdriver

driver = webdriver.Chrome()
```

Selenium automatically downloads correct driver.

No manual setup required.

---

# 13. Fix for Driver Version Error

Steps:

1. Delete `chromedriver.exe` if present in project folder.

Example before:

```
project
│
├── test_login.py
└── chromedriver.exe
```

After deleting:

```
project
│
└── test_login.py
```

2. Update Selenium:

```bash
pip install -U selenium
```

3. Run script again.

---

# 14. Python Environment Issues

Sometimes students install packages in one Python version but run scripts with another.

Example:

Python versions:

* Python 3.11
* Python 3.14

If Selenium is installed in 3.11 but script runs with 3.14 → error occurs.

Example error:

```
ModuleNotFoundError: No module named 'selenium'
```

Solution:

Install Selenium using:

```bash
python -m pip install selenium
```

This installs Selenium in the active Python environment.

---

# 15. Removing Extra Python Version

To remove Python 3.11:

1. Open **Windows Settings**
2. Go to **Apps**
3. Search **Python**
4. Select **Python 3.11**
5. Click **Uninstall**

Verify remaining version:

```bash
python --version
```

---

# 16. Best Practice for Selenium Setup

Always follow these rules:

1. Install latest Python
2. Install latest Selenium
3. Do not manually download drivers
4. Use Selenium automatic driver management

Example code:

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://google.com")
```
