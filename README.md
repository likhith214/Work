# Work

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Initialize WebDriver
driver = webdriver.Chrome()

# Open the target URL
driver.get('https://example.com')  # Replace with the actual URL

# Wait until the button is clickable and then click it
button = WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.CSS_SELECTOR, ".q-button.q-cta-button"))
)
button.click()

# Optionally, handle the redirect or interact with the new page
WebDriverWait(driver, 10).until(EC.url_changes(driver.current_url))

# Perform actions on the new page
# Example: new_element = driver.find_element(By.XPATH, "//your-new-element-xpath")

# Close the driver when done
driver.quit()
