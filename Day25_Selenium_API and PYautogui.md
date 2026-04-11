---
# 🧠 1. Introduction to Selenium APIs

## 📘 What is an API?

### 🪄 Analogy (Restaurant)
---
* You = Customer
* Kitchen = System
* Waiter = API

👉 You don’t go to kitchen directly
👉 You use waiter to communicate

✔ API = **medium to interact with system**

---

## 🧑‍💻 In Selenium

👉 APIs are **predefined methods** used to control browser

Example:

```python
driver.get("https://www.google.com")
element.click()
```

---

## 🔑 Types of Selenium APIs

### 1. Browser Control APIs

```python
driver.get()
driver.maximize_window()
driver.quit()
```

---

### 2. Element APIs

```python
driver.find_element(By.ID, "username")
```

---

### 3. Action APIs

```python
element.click()
element.send_keys("text")
```

---

### 4. Validation APIs

```python
element.is_displayed()
element.text
```

---

## 🎯 Key Point

👉 API = **What actions Selenium performs**

---

# ⚙️ 2. Selenium Architecture

## 🔄 Flow

```
Test Script → WebDriver → Browser Driver → Browser
```

---

## 🔍 Components

### 1. Test Script

Your Python code

---

### 2. Selenium WebDriver

* Core engine
* Converts commands

---

### 3. Browser Drivers

* ChromeDriver
* GeckoDriver

👉 Acts as translator

---

### 4. Browser

* Google Chrome
* Mozilla Firefox

---

## 🧠 Analogy

👉 Food delivery app

* You order → Script
* App → WebDriver
* Delivery → Driver
* Restaurant → Browser

---

# 🌐 3. Chrome & Firefox APIs

---

## ✅ Chrome API

```python
from selenium import webdriver
driver = webdriver.Chrome()
```

---

### ⚙️ Chrome Options (Capabilities)

```python
from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument("--start-maximized")
options.add_argument("--incognito")

driver = webdriver.Chrome(options=options)
```

---

### 🔥 Important Chrome Settings

```python
prefs = {
    "credentials_enable_service": False,
    "profile.password_manager_enabled": False,
    "profile.password_manager_leak_detection": False
}

options.add_experimental_option("prefs", prefs)
```

👉 Prevents:

* Save password popup
* Change password popup

---

## 🦊 Firefox API

```python
driver = webdriver.Firefox()
```

---

### ⚙️ Firefox Options

```python
from selenium.webdriver.firefox.options import Options

options = Options()
options.add_argument("--width=1200")
options.add_argument("--height=800")
```

---

## ⚠️ Difference

| Feature  | Chrome       | Firefox         |
| -------- | ------------ | --------------- |
| Maximize | Works        | Not reliable    |
| Speed    | Faster       | Slightly slower |
| Driver   | ChromeDriver | GeckoDriver     |

---

# 🧠 4. API vs Capability

| API                       | Capability                 |
| ------------------------- | -------------------------- |
| Action                    | Configuration              |
| Used after browser starts | Used before browser starts |
| Example: click()          | Example: incognito         |

---

## Example

```python
options.add_argument("--incognito")   # Capability
driver.get("https://example.com")     # API
```

---

# 🖱️ 5. PyAutoGUI Notes

## 📘 What is PyAutoGUI?

👉 Python library to control:

* Mouse
* Keyboard
* Screen

---

## 🪄 Analogy

👉 Acts like a **human using computer**

---

## 📦 Installation

```bash
pip install pyautogui
```

---

## ⚙️ Basic Functions

### 🖱️ Mouse

```python
pyautogui.moveTo(500, 500)
pyautogui.click()
pyautogui.rightClick()
```

---

### ⌨️ Keyboard

```python
pyautogui.write("Hello")
pyautogui.press("enter")
pyautogui.hotkey("ctrl", "s")
```

---

### 📸 Screenshot

```python
pyautogui.screenshot("img.png")
```

---

### 🔍 Image Recognition

```python
pyautogui.locateOnScreen("button.png")
```

---

# 🧠 Important Concepts

## 📍 Coordinates

* (0,0) = top-left
* Based on screen pixels

---

## ⏱️ Delay

```python
pyautogui.PAUSE = 1
```

---

## 🛑 Fail Safe

```python
pyautogui.FAILSAFE = True
```

👉 Move mouse to corner to stop script

---

# 🔥 Use Cases

* File upload popup
* Download dialog
* OS-level alerts

---

# ⚠️ Limitations of PyAutoGUI

❌ Not stable
❌ Depends on screen resolution
❌ Breaks if UI changes
❌ Slow
❌ Not suitable for CI/CD
❌ Difficult to maintain

---

# 🚫 Common Issues Faced

### 1. Wrong module import

❌ File named `pyautogui.py`

---

### 2. Case-sensitive functions

❌ `rightclick()`
✅ `rightClick()`

---

### 3. Chrome popups

* Save password
* Change password

👉 Fix using:

```python
--incognito
```

---

### 4. Save Image Issue

👉 “Save as” may:

* Open new tab
* Save `.tmp` file

---

## ✅ Fix
add
```python
time.sleep(5) #after clicking on save button
```

---

# 🧠 Important Learning

👉 PyAutoGUI works on **screen level**
👉 Selenium works on **DOM level**

---

# 🎯 Final Comparison

| Tool      | Usage               |
| --------- | ------------------- |
| Selenium  | Browser automation  |
| PyAutoGUI | OS-level automation |

---

# 🎓 Final Summary

👉 API = actions
👉 Capability = configuration
👉 Selenium = stable automation
👉 PyAutoGUI = human-like automation (less reliable)

---
