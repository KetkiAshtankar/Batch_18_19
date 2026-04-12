---

# 🧠 1. What are Exceptions in Selenium?

## 💡 Simple Definition:

 Exceptions = errors that occur during test execution

---

## 💬 Real-life analogy:

You go to a restaurant:

* Dish not available → ❌ *NoSuchElement*
* Waiter didn’t come → ❌ *Timeout*
* Table changed → ❌ *StaleElement*

👉 Selenium exceptions = real-world problems in automation

---

# 🏗️ 2. Selenium Exception Hierarchy (Python)

All exceptions come from:

```python
selenium.common.exceptions
```

Base class:

```
WebDriverException
```

---

# 🔥 3. MOST IMPORTANT EXCEPTIONS (with real examples)

---

# 🔹 3.1 NoSuchElementException

## ❌ Cause:

Element not found in DOM

## 🧪 Example:

```python
driver.find_element(By.ID, "wrong_id")
```

## 💥 Error:

```
NoSuchElementException
```

## ✅ Fix:

* Check locator
* Use waits

```python
WebDriverWait(driver,10).until(
    EC.presence_of_element_located((By.ID,"correct_id"))
)
```

---

# 🔹 3.2 TimeoutException

## ❌ Cause:

Wait condition not met in given time

## 🧪 Example:

```python
WebDriverWait(driver,5).until(
    EC.visibility_of_element_located((By.ID,"slow_element"))
)
```

## ✅ Fix:

* Increase wait
* Check if element actually appears

---

# 🔹 3.3 StaleElementReferenceException

## ❌ Cause:

Element refreshed / DOM updated

## 💡 Example:

* Page reload
* AJAX update

## 🧪 Example:

```python
element = driver.find_element(By.ID,"test")
driver.refresh()
element.click()   # ❌ stale
```

## ✅ Fix:

Re-find element:

```python
element = driver.find_element(By.ID,"test")
element.click()
```

---

# 🔹 3.4 ElementNotInteractableException

## ❌ Cause:

Element present but not clickable/visible

## 🧪 Example:

```python
driver.find_element(By.ID,"hidden_btn").click()
```

## ✅ Fix:

* Wait for visibility

```python
EC.element_to_be_clickable
```

---

# 🔹 3.5 ElementClickInterceptedException

## ❌ Cause:

Another element blocking click

## 💡 Example:

Popup covering button

## ✅ Fix:

* Scroll
* Close popup

```python
driver.execute_script("arguments[0].click();", element)
```

---

# 🔹 3.6 InvalidSelectorException

## ❌ Cause:

Wrong XPath / CSS

## 🧪 Example:

```python
driver.find_element(By.XPATH,"///wrong")
```

## ✅ Fix:

Correct syntax

---

# 🔹 3.7 NoSuchWindowException

## ❌ Cause:

Window/tab not found

## 🧪 Example:

```python
driver.switch_to.window("wrong")
```

## ✅ Fix:

Use correct handle

---

# 🔹 3.8 NoSuchFrameException

## ❌ Cause:

Frame not found

## 🧪 Example:

```python
driver.switch_to.frame("wrong_frame")
```

---

# 🔹 3.9 UnexpectedAlertPresentException

## ❌ Cause:

Alert appeared but not handled

## 🧪 Example:

Click triggers alert but no switch

## ✅ Fix:

```python
driver.switch_to.alert.accept()
```

---

# 🔹 3.10 MoveTargetOutOfBoundsException

## ❌ Cause:

ActionChains moved outside screen

---

# 🔹 3.11 JavascriptException

## ❌ Cause:

JS execution failed

---

# 🔹 3.12 SessionNotCreatedException

## ❌ Cause:

Browser-driver mismatch

## 💡 Example:

Chrome updated but driver old

---

# 🔹 3.13 WebDriverException

## ❌ Base exception (generic)

---

# 🧪 4. How to Handle Exceptions (VERY IMPORTANT)

---

## 🔹 Basic try-except

```python
from selenium.common.exceptions import NoSuchElementException

try:
    driver.find_element(By.ID,"test")
except NoSuchElementException:
    print("Element not found")
```

---

## 🔹 Multiple exceptions

```python
from selenium.common.exceptions import *

try:
    driver.find_element(By.ID,"test")
except (NoSuchElementException, TimeoutException):
    print("Handled error")
```

---

## 🔹 Best Practice (Real SDET way)

```python
def click_element(locator):
    try:
        WebDriverWait(driver,10).until(
            EC.element_to_be_clickable(locator)
        ).click()
    except Exception as e:
        print("Error:", e)
```

---

# 🧠 5. Explicit Wait vs Exceptions (VERY IMPORTANT CONCEPT)

👉 Good automation:

* Avoid exceptions using waits

👉 Bad automation:

* Catch everything blindly

---

## ❌ Wrong:

```python
try:
    driver.find_element(By.ID,"test").click()
except:
    pass
```

---

## ✅ Correct:

```python
WebDriverWait(driver,10).until(
    EC.element_to_be_clickable((By.ID,"test"))
).click()
```

---

# 🔥 6. Common Real-Time Scenarios

---

## 🔹 Scenario 1: Page loading slow

👉 Use TimeoutException handling

---

## 🔹 Scenario 2: Dynamic website

👉 Handle StaleElement

---

## 🔹 Scenario 3: Popup appears randomly

👉 Handle UnexpectedAlert

---

## 🔹 Scenario 4: Element hidden

👉 Use waits + scroll

---

# 💡 8. Golden Rules (VERY IMPORTANT)

### ✅ Rule 1:

> Use waits first, exceptions second

### ✅ Rule 2:

> Never use bare except

### ✅ Rule 3:

> Always log errors

### ✅ Rule 4:

> Re-locate elements after refresh

---


---

# 🧪 ✅ Handle ALL Alerts

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time

# Setup driver
driver = webdriver.Chrome()
driver.maximize_window()

# Open URL
driver.get("https://demoqa.com/alerts")

wait = WebDriverWait(driver, 10)

# -------------------------------
# 1. Simple Alert (Click me)
# -------------------------------
driver.find_element(By.ID, "alertButton").click()

alert = driver.switch_to.alert
print("Simple Alert Text:", alert.text)
alert.accept()

time.sleep(2)

# -------------------------------
# 2. Timer Alert (Appears after 5 sec)
# -------------------------------
driver.find_element(By.ID, "timerAlertButton").click()

wait.until(EC.alert_is_present())

alert = driver.switch_to.alert
print("Timer Alert Text:", alert.text)
alert.accept()

time.sleep(2)

# -------------------------------
# 3. Confirmation Alert
# -------------------------------
driver.find_element(By.ID, "confirmButton").click()

alert = driver.switch_to.alert
print("Confirm Alert Text:", alert.text)

alert.dismiss()   # Cancel
# alert.accept()  # OK (try both for students)

time.sleep(2)

# -------------------------------
# 4. Prompt Alert
# -------------------------------
driver.find_element(By.ID, "promtButton").click()

alert = driver.switch_to.alert
print("Prompt Alert Text:", alert.text)

alert.send_keys("Ketki")
alert.accept()

time.sleep(2)

# Close browser
driver.quit()
```

---


### ✅ `driver.switch_to.alert`

👉 MUST use this to handle alerts

---

### ✅ Alert Actions:

* `alert.accept()` → OK
* `alert.dismiss()` → Cancel
* `alert.send_keys()` → Input text

---

### ✅ Important Concept:

```python
wait.until(EC.alert_is_present())
```

👉 Needed for delayed alerts (very common in real apps)

---

# 💡 Common Mistakes 

❌ Not switching to alert
❌ Using `find_element` for alert
❌ Not waiting for delayed alert

---

---

## 💡 Analogy:

> Normal Selenium = pressing buttons
> ActionChains = using mouse like a human

---

## 🧪 Hands-on 1: Hover

Use:
👉 Selenium Web Alerts Demo (only for intro hovering if needed)

Or better:

```python
from selenium.webdriver.common.action_chains import ActionChains

actions = ActionChains(driver)
actions.move_to_element(element).perform()
```

---

## 🧪 Hands-on 2: Right Click

```python
actions.context_click(element).perform()
```

---

## 🧪 Hands-on 3: Double Click

```python
actions.double_click(element).perform()
```

---

---

# 🧪 ✅ Selenium Python Code – Drag & Drop

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
import time

# Setup driver
driver = webdriver.Chrome()
driver.maximize_window()

# Open URL
driver.get("https://practice.expandtesting.com/drag-and-drop")

# Create ActionChains object
actions = ActionChains(driver)

# Locate elements
source = driver.find_element(By.ID, "column-a")
target = driver.find_element(By.ID, "column-b")

# Perform drag and drop
actions.drag_and_drop(source, target).perform()

time.sleep(3)

driver.quit()
```

---

## ✅ 1. ActionChains

```python
actions = ActionChains(driver)
```

👉 Required for advanced mouse actions

---

## ✅ 2. Drag & Drop Method

```python
actions.drag_and_drop(source, target).perform()
```

👉 Combines:

* click + hold
* move
* release

---

# ⚠️ VERY IMPORTANT (Real-world issue)

👉 site sometimes **does NOT work with `drag_and_drop()`**

---

# 🧪 🔥 Alternative Method (Works when above fails)

```python
actions.click_and_hold(source)\
       .move_to_element(target)\
       .release()\
       .perform()
```




# 🧪 🔥 Code for "https://demoqa.com/droppable"

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
import time

# Initialize the driver
driver = webdriver.Chrome()

try:
    # Navigate to the droppable page
    driver.get("https://demoqa.com/droppable")
    time.sleep(3)

    # Find the draggable and droppable elements
    draggable = driver.find_element(By.ID, "draggable")
    droppable = driver.find_element(By.ID, "droppable")

    # Scroll the elements into view before dragging
    driver.execute_script("arguments[0].scrollIntoView({behavior: 'instant', block: 'center'});", draggable)
    driver.execute_script("arguments[0].scrollIntoView({behavior: 'instant', block: 'center'});", droppable)
    time.sleep(1)

    # Perform drag and drop with click-hold-move-release
    actions = ActionChains(driver)
    actions.move_to_element(draggable).click_and_hold(draggable)
    actions.move_to_element(droppable).pause(0.5).release().perform()
    time.sleep(2)

    # Verify the drop was successful
    result_text = droppable.text
    print(f"Result: {result_text}")

finally:
    driver.quit()
```


# 🧪 🔥 code for "https://jqueryui.com/droppable/"

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
import time

# Initialize the driver
driver = webdriver.Chrome()

try:
    # Navigate to the URL
    driver.get("https://jqueryui.com/droppable/")
    
    # Wait for page to load
    time.sleep(3)
    
    # Switch to iframe
    iframe = driver.find_element(By.TAG_NAME, "iframe")
    driver.switch_to.frame(iframe)
    
    # Wait for elements to be visible
    time.sleep(2)
    
    # Locate elements
    draggable = driver.find_element(By.ID, "draggable")
    droppable = driver.find_element(By.ID, "droppable")
    
    # Perform drag and drop
    actions = ActionChains(driver)
    actions.drag_and_drop(draggable, droppable).perform()
    
    # Wait to observe result
    time.sleep(2)
    
    print("Drag and drop completed successfully!")

finally:
    driver.quit()
```


# 🧪 🔥 Code for "https://practice.expandtesting.com/drag-and-drop-circles"

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.chrome.service import Service

try:
    # Initialize Chrome driver
    driver = webdriver.Chrome()
    driver.maximize_window()
    
    # Navigate to the website
    driver.get("https://practice.expandtesting.com/drag-and-drop-circles")
    
    try:
        # Wait for page to load
        time.sleep(2)
        
        # Find draggable circles and drop zones
        red = driver.find_element(By.CLASS_NAME, "red")
        green = driver.find_element(By.CLASS_NAME, "green")
        blue = driver.find_element(By.CLASS_NAME, "blue")
        
        # Find drop zones
        drop_zone = driver.find_element(By.ID, "target")
    
        
        # Create ActionChains object
        actions = ActionChains(driver)
        
        # Drag and drop circle 1 to drop zone 1
        actions.drag_and_drop(red, drop_zone).perform()
        time.sleep(1)
        
        # Drag and drop circle 2 to drop zone 2
        actions.drag_and_drop(green, drop_zone).perform()
        time.sleep(1)
        
        # Drag and drop circle 3 to drop zone 3
        actions.drag_and_drop(blue, drop_zone).perform()
        time.sleep(1)
        
        print("Drag and drop completed successfully!")
        
    except Exception as e:
        print(f"Error during drag and drop operations: {str(e)}")
    
    # Keep browser open for viewing results
    time.sleep(3)
    
except Exception as e:
    print(f"Error initializing driver or navigating to website: {str(e)}")

finally:
    try:
        driver.quit()
    except Exception as e:
        print(f"Error closing driver: {str(e)}")
```



