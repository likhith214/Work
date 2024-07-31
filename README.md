from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

# Setup Chrome driver
service = Service(ChromeDriverManager().install())
driver = webdriver.Chrome(service=service)

# Open the desired webpage
driver.get("URL_OF_YOUR_PAGE")

# Find the specific parent container
parent_container = driver.find_element(By.CSS_SELECTOR, ".tabs-content.active-section .vehicles-container")

# Find all vehicle-block divs within the specific parent container
vehicle_blocks = parent_container.find_elements(By.CSS_SELECTOR, ".vehicle-block")

# Loop through each vehicle-block and click on the a tag inside it
for block in vehicle_blocks:
    try:
        # Find the a tag within the current block
        a_tag = block.find_element(By.TAG_NAME, "a")
        
        # Perform the click
        ActionChains(driver).move_to_element(a_tag).click().perform()
        
        # Add any necessary wait time if needed
        # time.sleep(1)  # e.g., sleep for 1 second

        # Perform any additional actions after clicking the a tag if needed
        # For instance, navigate back to the original page if required
        # driver.back()
        
    except Exception as e:
        print(f"Could not click the a tag in this block: {e}")

# Close the driver
driver.quit()
