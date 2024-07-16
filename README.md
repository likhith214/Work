import requests
from bs4 import BeautifulSoup

# The URL of the webpage you want to scrape
url = 'URL_OF_THE_WEBPAGE'

# Send a GET request to fetch the raw HTML content
response = requests.get(url)

# Parse the HTML content
soup = BeautifulSoup(response.content, 'html.parser')

# Find the dropdown menu by its class
dropdown_menu = soup.find('ul', class_='dropdown-menu')

# Extract the options into a list
options = [li.get_text(strip=True) for li in dropdown_menu.find_all('li')]

# Print the extracted options
print(options)
