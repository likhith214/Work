from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

# Initialize the Chrome driver
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))

# Open the web page
driver.get('URL_OF_YOUR_PAGE')

# Find the input field and set its value
input_element = driver.find_element(By.ID, 'form_input_custom_dropdown_model-package')
input_element.clear()
input_element.send_keys('Paquete A Chasis Cabina')

# Perform any additional actions (e.g., submitting the form)

# Close the browser
driver.quit()
