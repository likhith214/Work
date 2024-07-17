from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Initialize the WebDriver
driver = webdriver.Chrome()  # or use webdriver.Firefox() for Firefox

# Open the target website
driver.get('URL_OF_THE_WEBSITE')

try:
    # Click the dropdown button to open the menu
    dropdown_button = WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.CLASS_NAME, 'dropdown-toggle'))
    )
    dropdown_button.click()

    # Wait for the dropdown menu to be visible
    dropdown_menu = WebDriverWait(driver, 10).until(
        EC.visibility_of_element_located((By.CLASS_NAME, 'dropdown-menu'))
    )

    # Select the desired option
    option_value = "Leasing"  # Change this to the desired option
    option = dropdown_menu.find_element(By.XPATH, f"//li[@data-sel='{option_value}']")
    option.click()

except Exception as e:
    print(f"An error occurred: {e}")
finally:
    # Close the browser
    driver.quit()
