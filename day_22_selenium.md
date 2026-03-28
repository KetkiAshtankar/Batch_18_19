---

# 📘 **Automation Testing with Selenium**

---

# 🔹 **1. Navigation in Selenium**

## 🧠 Concept:

Allows movement between web pages like a real browser.

## 📌 Methods:

```python
driver.get("https://example.com")   # Open URL
driver.back()                       # Go back
driver.forward()                    # Go forward
driver.refresh()                    # Refresh page
```

## 🧠 Key Point:

* Browser maintains **history stack**
* Selenium controls navigation programmatically

---

# 🔹 **2. Headless Browser**

## 🧠 Concept:

Run browser **without UI**

## 💻 Code:

```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

options = Options()
options.add_argument("--headless")

driver = webdriver.Chrome(options=options)
driver.get("https://www.google.com")

print(driver.title)
driver.quit()
```

## ✅ Advantages:

* Faster execution
* Used in CI/CD (Jenkins)

## ❌ Disadvantages:

* Hard to debug
* Some elements behave differently

---

# 🔹 **3. Chrome Options (Very Important)**

## 🧠 Concept:

Customize browser behavior before launch

---

## ✅ Common Options:

### Incognito Mode

```python
options.add_argument("--incognito")
```

### Maximize / Window Size

```python
options.add_argument("--start-maximized")
options.add_argument("--window-size=1920,1080")
```

### Disable Notifications

```python
options.add_argument("--disable-notifications")
```

### Disable Extensions

```python
options.add_argument("--disable-extensions")
```

### Ignore SSL Errors

```python
options.add_argument("--ignore-certificate-errors")
```

---

---

# 🔹 **4. Dropdown Handling**

## 🧠 Works only for `<select>` tag

---

## 💻 Setup:

```python
from selenium.webdriver.support.ui import Select

dropdown = Select(driver.find_element(By.ID, "dropdown"))
```

---

## ✅ Methods:

### Select by Visible Text

```python
dropdown.select_by_visible_text("Option 1")
```

### Select by Value

```python
dropdown.select_by_value("2")
```

### Select by Index

```python
dropdown.select_by_index(1)
```

---

## 🔥 Useful Operations:

### Get All Options

```python
for option in dropdown.options:
    print(option.text)
```

### Get Selected Option

```python
dropdown.first_selected_option.text
```

### Validate Selection

```python
assert dropdown.first_selected_option.text == "Option 1"
```

---

## ❌ When Select won’t work:


👉 Use:

```python
element.click()
```

---

# 🔹 **5. Scrolling using JavaScript**

## 🧠 Why needed:

Selenium can only interact with **visible elements**

---

## 💻 Scroll Methods:

### Scroll to Bottom

```python
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
```

### Scroll to Element

```python
driver.execute_script("arguments[0].scrollIntoView();", element)
```

### Scroll by Pixels

```python
driver.execute_script("window.scrollBy(0, 500);")
```

---

## 🔥 Best Practice:

```python
driver.execute_script("arguments[0].scrollIntoView({block: 'center'});", element)
element.click()
```

---

# 🔹 **6. Pytest – Testing Framework**

## 🧠 Purpose:

* Run tests
* Validate results
* Generate reports

---

## 📁 Naming Rule:

```text
test_file.py
```

---

## 💻 Basic Test:

```python
def test_google_title():
    driver = webdriver.Chrome()
    driver.get("https://www.google.com")

    assert "Google" in driver.title

    driver.quit()
```

---

## ▶️ Run:

```bash
pytest test_file.py
```

---

# 🔹 **7. Assertions**

## 🧠 Concept:

Validates expected vs actual result

---

## ✅ Examples:

```python
assert "Google" in driver.title
assert driver.current_url == "https://www.google.com/"
assert element.is_displayed()
assert element.text == "Login"
```

---

## ❌ If assertion fails:

👉 Test stops immediately

---

# 🔹 **8. Fixtures (VERY IMPORTANT)**

## 🧠 Problem:

Repeating driver setup

---

## ✅ Solution:

```python
import pytest
from selenium import webdriver

@pytest.fixture
def setup():
    driver = webdriver.Chrome()
    yield driver
    driver.quit()
```

---

## 💻 Usage:

```python
def test_example(setup):
    setup.get("https://www.google.com")
    assert "Google" in setup.title
```

---

## 🧠 Key Concept:

| Keyword     | Meaning        |
| ----------- | -------------- |
| fixture     | setup function |
| yield       | return control |
| after yield | teardown       |

---

# 🔹 **9. Multiple Tests**

```python
def test_google(setup):
    setup.get("https://www.google.com")

def test_amazon(setup):
    setup.get("https://www.amazon.in")
```

👉 Pytest runs all automatically

---

# 🔹 **10. Integration Example (Real Test)**

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select

@pytest.fixture
def setup():
    driver = webdriver.Chrome()
    yield driver
    driver.quit()

def test_dropdown(setup):
    setup.get("https://the-internet.herokuapp.com/dropdown")

    dropdown = Select(setup.find_element(By.ID, "dropdown"))
    dropdown.select_by_visible_text("Option 1")

    assert dropdown.first_selected_option.text == "Option 1"
```

---

# 🔹 **11. Running Tests**

```bash
pytest -v
```

👉 Shows detailed output

---

# 🔹 **12. Pytest Marks **

```python
import pytest

@pytest.mark.smoke
def test_google(setup):
    pass
```

Run:

```bash
pytest -m smoke
```

---

# 🔹 **13. Common Mistakes**

❌ Wrong file name → test won’t run
❌ Not passing options → no effect
❌ Using Select on custom dropdown
❌ Forgetting `yield` in fixture
❌ Hardcoding `sleep()`

---

# 🔹 **14. Summary**

👉 Selenium = Performs actions
👉 Pytest = Validates actions

👉 Options = Controls browser behavior
👉 JavaScript = Handles difficult UI cases

---
