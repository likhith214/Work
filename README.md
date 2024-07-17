from bs4 import BeautifulSoup

html = """
<form id="exampleForm">
    <ul>
        <li>Option 1</li>
        <li>Option 2</li>
        <li>Option 3</li>
    </ul>
</form>
"""

soup = BeautifulSoup(html, 'html.parser')

# Find the form by its ID
form = soup.find('form', {'id': 'exampleForm'})

# Find all li tags within the form
options = form.find_all('li')

# Extract the text from each li tag
option_texts = [option.get_text() for option in options]

print(option_texts)
