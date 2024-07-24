from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Initialize the WebDriver and navigate to the website
driver = webdriver.Chrome()  # or use another driver
driver.get("URL_OF_YOUR_WEBSITE")

try:
    # Wait until the radio buttons are present
    radio_buttons = WebDriverWait(driver, 10).until(
        EC.presence_of_all_elements_located((By.CSS_SELECTOR, ".custom-radio"))
    )

    # Ensure there are at least two radio buttons
    if len(radio_buttons) >= 2:
        # Use JavaScript to click the second radio button
        driver.execute_script("arguments[0].click();", radio_buttons[1])
    else:
        print("Less than two radio buttons found.")
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    driver.quit()
