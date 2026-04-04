---

# 🧠 1. Introduction to Browser Capabilities
---
## Analogy
Think of launching a browser like **booking a cab** 
When you book a cab, you give preferences:

* AC or non-AC
* Music or silent
* Window seat
* No toll roads

👉 These preferences = **Capabilities**

So when Selenium launches a browser, you tell it:

* Open in **incognito**
* Ignore **SSL errors**
* Disable **notifications**
* Run **headless**
* Maximize window

👉 These instructions = **Browser Capabilities**

---

## 👨‍💻 Technical Explanation

**Browser Capabilities** are a set of key-value pairs used to configure browser behavior at runtime.

They are:

* Used during **WebDriver session creation**
* Define how the browser should behave
* Passed using:

  * `Options` classes (recommended)
  * Previously: `DesiredCapabilities` (now mostly merged into Options)

---

# 🧪 2. Types of Capabilities

## 🔹 Common (All Browsers)

* `acceptInsecureCerts` → Ignore SSL errors
* `pageLoadStrategy` → eager / normal / none
* `unhandledPromptBehavior` → accept / dismiss alerts

---

## 🔹 Browser-specific

### 🟠 Chrome (ChromeOptions)

* `--incognito`
* `--disable-notifications`
* `--start-maximized`
* `--disable-popup-blocking`
* `--ignore-certificate-errors`

---

### 🟣 Firefox (FirefoxOptions)

* `-private`
* `dom.webnotifications.enabled = false`
* `acceptInsecureCerts = true`

---

### 🔵 Edge (EdgeOptions)

(Same as Chrome because Edge is Chromium-based)

* `--inprivate`
* `--disable-notifications`
* `--ignore-certificate-errors`

---

# 🧾 3. All Important Capabilities an SDET Should Know

## 🌐 Browser Behavior

* Incognito / Private mode
* Headless execution
* Window size
* Disable extensions

## 🔐 Security

* Ignore SSL certificates
* Allow insecure content

## 🔔 Notifications & Popups

* Disable notifications
* Disable geolocation popups
* Disable permission dialogs

## ⚡ Performance

* Page load strategy
* Disable GPU
* Disable images (advanced)

## 🧪 Debugging

* Enable logs
* Console logs
* Network logs

---

# 🧩 4. FULL CODE (Same Behavior in Chrome, Firefox, Edge)

👉 Scenario:

* Open **[https://www.saucedemo.com/](https://www.saucedemo.com/)**
* Incognito / Private
* Ignore SSL errors
* Disable notifications
* Disable popups
* Maximize window
* Quit properly

---

# 🟠 CHROME CODE

```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
import time

chrome_options = Options()

# Capabilities
chrome_options.add_argument("--incognito")
chrome_options.add_argument("--start-maximized")
chrome_options.add_argument("--disable-notifications")
chrome_options.add_argument("--disable-popup-blocking")
chrome_options.add_argument("--ignore-certificate-errors")

driver = webdriver.Chrome(options=chrome_options)

driver.get("https://www.saucedemo.com/")

time.sleep(3)

driver.quit()
```

---

# 🟣 FIREFOX CODE

```python
from selenium import webdriver
from selenium.webdriver.firefox.options import Options
import time

firefox_options = Options()

# Capabilities
firefox_options.add_argument("-private")
firefox_options.set_preference("dom.webnotifications.enabled", False)
firefox_options.set_preference("dom.disable_open_during_load", True)
firefox_options.accept_insecure_certs = True

driver = webdriver.Firefox(options=firefox_options)

driver.maximize_window()
driver.get("https://www.saucedemo.com/")

time.sleep(3)

driver.quit()
```

---

# 🔵 EDGE CODE

```python
from selenium import webdriver
from selenium.webdriver.edge.options import Options
import time

edge_options = Options()

# Capabilities
edge_options.add_argument("--inprivate")
edge_options.add_argument("--start-maximized")
edge_options.add_argument("--disable-notifications")
edge_options.add_argument("--disable-popup-blocking")
edge_options.add_argument("--ignore-certificate-errors")

driver = webdriver.Edge(options=edge_options)

driver.get("https://www.saucedemo.com/")

time.sleep(3)

driver.quit()
```

---

# 🔄 5. Same Output Across All Browsers

✔ Opens SauceDemo
✔ Runs in private/incognito
✔ No notifications
✔ No popups
✔ Ignores SSL issues
✔ Maximized window
✔ Closes properly (`driver.quit()`)

---

# ⚠️ Important Interview Points

👉 Difference:

* `driver.close()` → closes one tab
* `driver.quit()` → closes entire browser session ✅ (Always use this)

👉 Modern Selenium:

* Prefer `Options` over `DesiredCapabilities`

👉 Edge = Chrome (Chromium-based)

---
Code to Configure download:
```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
import time
from selenium.webdriver.common.by import By
import os

download_path = os.path.join(os.getcwd(), "chromedownloads")
os.makedirs(download_path, exist_ok=True)

chrome_options = Options()
chrome_options.add_argument("--start-maximized")
chrome_options.add_argument("--disable-notifications")

prefs = {
    "download.default_directory": download_path,
    "download.prompt_for_download": False,
    "download.directory_upgrade": True,
}
chrome_options.add_experimental_option("prefs", prefs)

driver = webdriver.Chrome(options=chrome_options)
driver.get("https://practice.expandtesting.com/download")
time.sleep(3)
link =driver.find_element(By.LINK_TEXT,"1775220960873_DNDAgentFile.txt")
print(link.text)
driver.execute_script("arguments[0].scrollIntoView(true);", link)
time.sleep(2)
driver.execute_script("arguments[0].click();", link)
time.sleep(5)
print("File downloaded successfully to: ", download_path)
time.sleep(5)
driver.quit()
```
