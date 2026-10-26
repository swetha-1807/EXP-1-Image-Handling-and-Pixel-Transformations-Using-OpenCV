# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV

Name: SWETHA K  
Register Number: 212224230284

## Aim

To develop a Python program using OpenCV to perform basic image processing operations, including reading and displaying images, drawing geometric shapes, adding text, converting color spaces, manipulating pixels, resizing, cropping, and flipping images.

## Software Required

1. Anaconda – Python 3.7
2. Jupyter Notebook
3. OpenCV library
4. Matplotlib library

## Algorithm

Step 1: Import the required libraries, OpenCV and Matplotlib, for image processing and visualization.

Step 2: Read an image from the local directory using OpenCV and display the original image using Matplotlib.

Step 3: Draw geometric shapes, such as a line, circle, and rectangle, on the image using OpenCV functions.

Step 4: Add text to the image using the `cv2.putText()` function and display the modified image.

Step 5: Convert the original image into different color spaces, including RGB, HSV, grayscale, and YCrCb, using the appropriate OpenCV functions.

Step 6: Modify selected pixels in the image by assigning new pixel values to a specified region.

Step 7: Resize the image to a smaller dimension using the `cv2.resize()` function.

Step 8: Extract a specific region of the image using array slicing to perform image cropping.

Step 9: Flip the image horizontally and vertically using the `cv2.flip()` function.

Step 10: Display the processed images with suitable titles using Matplotlib.

## Program Developed By

Name: SWETHA K 
Register Number: 212224230284

### Step 1: Import Libraries and Load the Image

```
.import cv2
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread(
    r'C:\Users\admin\Downloads\my photo dipt.jpeg'
)

if img is not None:
    # Convert BGR to RGB
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Display the image
    plt.imshow(img_rgb)
    plt.title("Original Image")
    plt.axis('off')
    plt.show()
else:
    print("Image not found. Please check the file path.")
```

<img width="408" height="552" alt="image" src="https://github.com/user-attachments/assets/0487d77d-2de9-4ed7-a7a8-1c47151d9cf5" />



### Step 2: Draw Geometric Shapes

#### 2.1 Drawing a Line

```
img = cv2.imread(
    r'C:\Users\admin\Downloads\my photo dipt.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Draw a line from top-left to bottom-right
line_img = cv2.line(
    img_rgb,
    (0, 0),
    (width - 1, height - 1),
    (255, 0, 0),
    2
)
# Display the image
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()

```
<img width="357" height="525" alt="image" src="https://github.com/user-attachments/assets/abb828fc-60f2-4abb-9bfc-9fcf8130a69a" />


#### 2.2 Drawing a Circle

```
img = cv2.imread(
    r'C:\Users\admin\Downloads\my photo dipt.jpeg'
)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img_rgb.shape

circle_img = cv2.circle(img_rgb,(470,600),100,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)
# Display the image
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```
<img width="370" height="512" alt="image" src="https://github.com/user-attachments/assets/e14a7961-cae3-4a82-8e3e-375d1cc7ea51" />

#### 2.3 Drawing a Rectangle

```
image = cv2.imread(r'C:\Users\admin\Downloads\my photo dipt.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(
    img_rgb.copy(),
    (0, 0),
    (width - 1, height - 1),
    (255, 0, 0),
    10
)
# Display the image
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```

<img width="373" height="527" alt="image" src="https://github.com/user-attachments/assets/c29b9180-eaf9-4d94-ab92-59c5e7a04923" />


#### 2.4 Adding Text

```
img = cv2.imread(
    r'C:\Users\admin\Downloads\my photo dipt.jpeg'
)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 0, 0), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)


# Display the image
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```
<img width="372" height="532" alt="image" src="https://github.com/user-attachments/assets/7f3e8b98-c439-4535-a055-06f40a4a0273" />


### Step 3: Color Space Conversion

```
img = cv2.imread(
    r'C:\Users\admin\Downloads\my photo dipt.jpeg'
)

# Check whether the image loaded successfully
if img is None:
    print("Error: Image not found. Check the file path.")

else:
    # Convert BGR to RGB
    image_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Original RGB Image
    plt.figure(figsize=(15, 8))

    plt.subplot(2, 3, 1)
    plt.imshow(image_rgb)
    plt.title("Original RGB Image")
    plt.axis("off")

    # Convert RGB to HSV
    image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

    plt.subplot(2, 3, 2)
    plt.imshow(image_hsv)
    plt.title("HSV Image")
    plt.axis("off")

    # Convert RGB to Grayscale
    image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

    plt.subplot(2, 3, 3)
    plt.imshow(image_gray, cmap='gray')
    plt.title("Grayscale Image")
    plt.axis("off")

    # Convert RGB to YCrCb
    image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

    plt.subplot(2, 3, 4)
    plt.imshow(image_ycrcb)
    plt.title("YCrCb Image")
    plt.axis("off")

    # Convert HSV back to RGB
    image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

    plt.subplot(2, 3, 5)
    plt.imshow(image_hsv_to_rgb)
    plt.title("HSV to RGB Image")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

<img width="882" height="602" alt="image" src="https://github.com/user-attachments/assets/002759a1-2f3f-48e4-9aac-c288dd16d5d8" />


### Step 4: Pixel Manipulation

```
if img is None:
    print("Error: Image not loaded. Please check the file path.")

else:
    # Modify a 300x300 block of pixels to white
    img[475:775, 315:615] = [255, 255, 255]

    # Convert BGR to RGB for displaying with Matplotlib
    image_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Display the modified image
    plt.imshow(image_rgb)
    plt.title("Image with 300x300 White Block")
    plt.axis("off")
    plt.show()

```

<img width="402" height="522" alt="image" src="https://github.com/user-attachments/assets/2921d0a1-3b90-4b5a-b1da-ea386a2ea00e" />


### Step 5: Image Resizing

```
img = cv2.imread(r'C:\Users\admin\Downloads\my photo dipt.jpeg')
# Check whether the image loaded successfully
if img is None:
    print("Error: Image not found. Check the file path.")

else:
    # Get the original image dimensions
    height, width = img.shape[:2]

    print("Original image dimensions:", width, "x", height)

    # Resize the image to half its original size
    resized_image = cv2.resize(
        img,
        (width // 2, height // 2)
    )

    # Convert BGR to RGB for displaying with Matplotlib
    resized_image_rgb = cv2.cvtColor(
        resized_image,
        cv2.COLOR_BGR2RGB
    )

    # Display the resized image dimensions
    print("Resized image dimensions:", resized_image_rgb.shape)

    # Display the resized image
    plt.imshow(resized_image_rgb)
    plt.title("Resized Image (Half Size)")
    plt.axis("off")
    plt.show()
```

<img width="617" height="577" alt="image" src="https://github.com/user-attachments/assets/cdbf0b1b-5c06-4925-9cb7-39c560ba3268" />


### Step 6: Image Cropping

```
image = cv2.imread(r'C:\Users\admin\Downloads\my photo dipt.jpeg')

image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```
<img width="491" height="532" alt="image" src="https://github.com/user-attachments/assets/4826dafc-5e95-4baf-b2b8-2f77d6f7e98b" />


### Step 7: Image Flipping

```
image = cv2.imread(r'C:\Users\admin\Downloads\my photo dipt.jpeg')

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")

# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")

```
<img width="797" height="545" alt="image" src="https://github.com/user-attachments/assets/b5f542ba-b65a-4619-87f0-fef945762b83" />

```
image = cv2.imread(r'C:\Users\admin\Downloads\my photo dipt.jpeg')

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally,
    cv2.COLOR_BGR2RGB
)

# Display horizontally flipped image
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()

```
<img width="372" height="517" alt="image" src="https://github.com/user-attachments/assets/879eb000-346e-4d56-9355-3a57bef20a4c" />


## Result

Thus, the Python program was implemented successfully using OpenCV to perform basic image processing operations, including image reading and display, geometric shape drawing, text insertion, color space conversion, pixel manipulation, resizing, cropping, and horizontal and vertical flipping.
