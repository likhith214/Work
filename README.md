import pytesseract
from PIL import Image, ImageEnhance, ImageFilter

def preprocess_image(image_path):
    # Open the image file
    img = Image.open(image_path)
    
    # Convert to grayscale
    img = img.convert('L')
    
    # Enhance the image
    enhancer = ImageEnhance.Contrast(img)
    img = enhancer.enhance(2)
    
    # Apply a median filter to reduce noise
    img = img.filter(ImageFilter.MedianFilter())
    
    # Save the processed image (optional)
    img.save('processed_image.png')
    
    return img

def solve_captcha(image_path):
    # Preprocess the image
    processed_image = preprocess_image(image_path)
    
    # Use Tesseract to extract text
    captcha_text = pytesseract.image_to_string(processed_image, config='--psm 8')
    
    # Convert text to lower case and remove whitespace
    captcha_text = captcha_text.lower().strip()
    
    return captcha_text

# Example usage
captcha_text = solve_captcha('captcha_image.png')
print(f'Solved CAPTCHA text: {captcha_text}')
