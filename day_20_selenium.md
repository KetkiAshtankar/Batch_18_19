# Python Selenium + Pytest Notes

# 1. What is Pytest

### Explanation

Pytest is a **testing framework** used to automatically check if our code works correctly.

Instead of manually running functions and checking output, pytest:

* Runs tests automatically
* Shows passed/failed results
* Generates reports
* Helps organize test cases

Example idea:

If we write a function:

```python
def add(a,b):
    return a+b
```

We can test it automatically.

```python
def test_add():
    assert add(2,3)==5
```

pytest will verify whether the result is correct.

---

# 2. Pytest Naming Rules

Pytest discovers tests using naming conventions.

### File Name

```
test_login.py
test_math.py
```

### Function Name

```
def test_login():
```

If the name does not follow the rule, pytest will **not execute it**.

---

# 3. Running Pytest

Basic command

```
pytest
```

Run with detailed output

```
pytest -v
```

Example output

```
test_login.py::test_login PASSED
```

---

# 4. Important Pytest Flags

## -v (Verbose)

Shows detailed output.

```
pytest -v
```

Output

```
test_add PASSED
test_sub PASSED
```

---

## -s

Shows **print statements in terminal**

Example

```python
def test_title():
    print("Test started")
```

Run

```
pytest -s
```

Output

```
Test started
```

Without `-s` pytest hides prints.

---

## -k

Run specific test by keyword.

Example

```
pytest -k "login"
```

Runs only tests containing **login**.

Example

```
test_login_valid
test_login_invalid
```

---

## -m (markers)

Run tests using markers.

Example

```python
@pytest.mark.smoke
def test_login():
```

Run

```
pytest -m smoke
```

---

---

# 5. Running Specific Test File

Run full file

```
pytest test_login.py
```

---

Run specific test function

```
pytest test_login.py::test_invalid_login
```

---

# 6. Pytest HTML Reports

Install plugin

```
pip install pytest-html
```

Run command

```
pytest --html=report.html
```

Report file will be created.

Open

```
report.html
```

in browser.

---

# 7. Changing Report Name

Example

```
pytest --html=login_report.html
```

or

```
pytest --html=smoke_report.html
```

---

# 8. Combining Commands

Example

```
pytest -v -s --html=report.html
```

Meaning

| Flag   | Purpose        |
| ------ | -------------- |
| -v     | verbose output |
| -s     | show prints    |
| --html | create report  |

---

# 9. Example Selenium Pytest Test

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By

def test_invalid_login():

    driver = webdriver.Chrome()

    driver.get("https://www.saucedemo.com")

    username=driver.find_element(By.ID,"user-name")
    username.send_keys("wrong_user")

    password=driver.find_element(By.ID,"password")
    password.send_keys("wrong_pass")

    driver.find_element(By.ID,"login-button").click()

    error=driver.find_element(By.CLASS_NAME,"error-message-container").text

    assert "Epic sadface" in error

    driver.quit()
```

---

# 10. Why Print Does Not Appear in HTML Report

Example

```
print(driver.title)
```

It appears only in **terminal**.

Reason:

pytest-html **does not capture print output by default**.

Solution → use logging.

---

# 11. Using Logging in Tests

Import logging

```python
import logging
```

Configure logging

```python
logging.basicConfig(level=logging.INFO)
```

Example

```python
logging.info(driver.title)
```

Run

```
pytest --log-cli-level=INFO
```

---

# 12. Common Pytest Errors

## Error 1

```
NameError: pytest is not defined
```

Reason

```
@pytest.mark.smoke
```

but pytest not imported.

Fix

```python
import pytest
```

---

## Error 2

```
int object is not callable
```

Example mistake

```python
print = 10
print("Hello")
```

Fix

Do not override built-in functions.

---
