# Day 12 - 06-10-2026
# Registration Form Assignment II

### Code:
```
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from webdriver_manager.chrome import ChromeDriverManager

def auto_fill_selenium_form():
    options = webdriver.ChromeOptions()
    options.add_experimental_option("detach", True)
    driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)
    wait = WebDriverWait(driver, 15)

    driver.get("https://vinothqaacademy.com/demo-site/")
    driver.maximize_window()

    first_name = wait.until(EC.visibility_of_element_located((By.ID, "vfb-5")))
    first_name.send_keys("Suriya")
    print("First Name:", first_name.get_attribute("value"))

    last_name = driver.find_element(By.ID, "vfb-7")
    last_name.send_keys("M")
    print("Last Name:", last_name.get_attribute("value"))

    gender = driver.find_element(By.XPATH, "//input[@type='radio' and @value='Male']")
    if not gender.is_selected():
        driver.execute_script("arguments[0].click();", gender)
    print("Gender selected:", gender.is_selected())

    selenium_checkbox = driver.find_element(By.XPATH, "//input[@type='checkbox' and @value='Selenium WebDriver']")
    if not selenium_checkbox.is_selected():
        driver.execute_script("arguments[0].click();", selenium_checkbox)
    print("Selenium selected:", selenium_checkbox.is_selected())

    street = driver.find_element(By.XPATH, "//input[contains(@id,'address') and not(contains(@id,'address-2'))]")
    street.send_keys("123 Main Street")
    print("Street:", street.get_attribute("value"))

    address2 = driver.find_element(By.XPATH, "//input[contains(@id,'address-2')]")
    address2.send_keys("Room 101")
    print("Address 2:", address2.get_attribute("value"))

    city = driver.find_element(By.XPATH, "//input[contains(@id,'city')]")
    city.send_keys("Chennai")
    print("City:", city.get_attribute("value"))

    state = driver.find_element(By.XPATH, "//input[contains(@id,'state')]")
    state.send_keys("Tamil Nadu")
    print("State:", state.get_attribute("value"))

    zip_code = driver.find_element(By.XPATH, "//input[contains(@id,'zip')]")
    zip_code.send_keys("600001")
    print("Postal Code:", zip_code.get_attribute("value"))

    email = wait.until(EC.visibility_of_element_located((By.ID, "vfb-14")))
    email.send_keys("suriya@example.com")
    print("Email:", email.get_attribute("value"))

    print("\nFORM FILLED SUCCESSFULLY")
    print("No submit button clicked.")
    print("Browser will remain open.")

    time.sleep(60)

if __name__ == "__main__":
    auto_fill_selenium_form()
```

### Output:

<img width="1465" height="817" alt="image" src="https://github.com/user-attachments/assets/97741e5c-9828-47e9-b16d-5432ac9e3b06" />


