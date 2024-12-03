from PIL import Image, ImageDraw, ImageFont
import io
from google.colab import files

# Step 1: Upload the image
print("Please upload your image (use a small size for faster processing):")
uploaded = files.upload()

# Load the uploaded image
image_path = list(uploaded.keys())[0]
image = Image.open(io.BytesIO(uploaded[image_path]))

# Step 2: Resize the image for better performance
print("Resizing the image for optimization...")
image = image.resize((500, 500))  # Optimized for mobile processing (500x500)

# Step 3: Function to add text behind the image
def add_text_behind_image(image, text, position=(50, 50)):
    # Create a transparent overlay
    overlay = Image.new("RGBA", image.size, (255, 255, 255, 0))
    draw = ImageDraw.Draw(overlay)

    # Use the default font for compatibility
    font = ImageFont.load_default()

    # Draw text with transparency
    draw.text(position, text, fill=(255, 255, 255, 150), font=font)

    # Merge the original image with the overlay
    return Image.alpha_composite(image.convert("RGBA"), overlay)

# Step 4: Input the text
text_to_add = input("Enter the text to add behind the image: ")

# Step 5: Process the image
print("Processing the image...")
processed_image = add_text_behind_image(image, text_to_add, position=(100, 100))

# Step 6: Display and save the processed image
print("Displaying the processed image...")
processed_image.show()

# Save and download the image
output_path = "processed_image.png"
processed_image.save(output_path)
print("Image processed and saved. Downloading now...")
files.download(output_path)
