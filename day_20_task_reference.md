# Similar Selenium + Pytest Practice Question

### Task

Visit the URL:

[https://the-internet.herokuapp.com/login](https://the-internet.herokuapp.com/login)
(Website: The Internet Herokuapp)

Login using the following credentials:

```
Username: tomsmith
Password: SuperSecretPassword!
```

---

## Using Python Selenium perform the following:

1. Open the browser and navigate to the website.
2. Print the **title of the webpage**.
3. Print the **current URL of the webpage**.
4. After login, capture the **success message**.
5. Extract the **entire webpage source** and save it in a file named:

```
heroku_login_page.txt
```

---

## After completing Selenium automation create **Pytest test cases**

Generate reports for the following cases:

### Positive Test Case

Verify:

1. Correct login redirects to **secure area page**
2. URL contains **/secure**
3. Success message appears

---

### Negative Test Case

Verify:

1. Login with incorrect password
2. Error message appears

---

# Solution

## Selenium Script

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()

driver.get("https://the-internet.herokuapp.com/login")

# Print Title
print("Title:", driver.title)

# Print URL
print("Current URL:", driver.current_url)

# Login
username = driver.find_element(By.ID, "username")
username.send_keys("tomsmith")

password = driver.find_element(By.ID, "password")
password.send_keys("SuperSecretPassword!")

driver.find_element(By.CSS_SELECTOR, "button[type='submit']").click()

time.sleep(2)

# Success message
message = driver.find_element(By.ID, "flash").text
print("Login Message:", message)

# Save page source
page_content = driver.page_source

file = open("heroku_login_page.txt", "w", encoding="utf-8")
file.write(page_content)
file.close()

driver.quit()
```

---

# Pytest Automation Tests

## Positive Test

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By

@pytest.mark.positive
def test_valid_login():

    driver = webdriver.Chrome()
    driver.get("https://the-internet.herokuapp.com/login")

    driver.find_element(By.ID,"username").send_keys("tomsmith")
    driver.find_element(By.ID,"password").send_keys("SuperSecretPassword!")
    driver.find_element(By.CSS_SELECTOR,"button[type='submit']").click()

    assert "secure" in driver.current_url

    message = driver.find_element(By.ID,"flash").text
    assert "You logged into a secure area!" in message

    driver.quit()
```

---

# Negative Test Case

```python
@pytest.mark.negative
def test_invalid_login():

    driver = webdriver.Chrome()
    driver.get("https://the-internet.herokuapp.com/login")

    driver.find_element(By.ID,"username").send_keys("tomsmith")
    driver.find_element(By.ID,"password").send_keys("wrongpassword")
    driver.find_element(By.CSS_SELECTOR,"button[type='submit']").click()

    error = driver.find_element(By.ID,"flash").text

    assert "Your password is invalid!" in error

    driver.quit()
```

---

# Generate Pytest HTML Report

Run command:

```
pytest -v -s --html=login_report.html
```

This will generate a report file.

---

# Expected Validations

| Test Case     | Expected Result         |
| ------------- | ----------------------- |
| Valid login   | Redirect to secure page |
| URL check     | Contains `/secure`      |
| Invalid login | Error message displayed |

---
