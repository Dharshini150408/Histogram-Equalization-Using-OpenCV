# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.


### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.


### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.
```
plt.imshow(img_eq, cmap='gray')
plt.title('Equalized Rose Image')
plt.axis('off')
plt.show()

```
### Step 6:
Read the same image in color format.
```
img = cv2.imread('rose.jpg', cv2.IMREAD_COLOR)

plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Rose Image')
plt.axis('off')
plt.show()

img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

```
### Step 7:
Split the image into B, G, R channels and plot their histograms.
```
img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])
```
### Step 8:
Convert the image from BGR to HSV color space.
```
img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)
```
### Step 9:
Apply histogram equalization on the V (Value) channel.
```
plt.figure(figsize=(10,5))

plt.subplot(121)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Rose Image')
plt.axis('off')

plt.subplot(122)
plt.imshow(cv2.cvtColor(img_eq, cv2.COLOR_BGR2RGB))
plt.title('Equalized Rose Image')
plt.axis('off')

plt.show()
```

### Step 10:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.
```
plt.figure(figsize=(12,10))

plt.subplot(221)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Rose Image')
plt.axis('off')

plt.subplot(222)
plt.imshow(cv2.cvtColor(img_eq, cv2.COLOR_BGR2RGB))
plt.title('Equalized Rose Image')
plt.axis('off')

plt.subplot(223)
plt.hist(img.ravel(), 256, range=[0,256])
plt.title('Original Histogram')

plt.subplot(224)
plt.hist(img_eq.ravel(), 256, range=[0,256])
plt.title('Equalized Histogram')

plt.show()
```
---

## Program
## Grayscale Histogram Equlaization
```

# Read the image in grayscale
gray = cv2.imread('parrot.jpg', 0)

# Check whether image is loaded
if gray is None:
    print("Image not found. Check the file name and folder.")
else:
    # Display original grayscale image and histogram
    plt.figure(figsize=(10, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(gray, cmap='gray')
    plt.title('Original Grayscale Image')
    plt.axis('off')

    plt.subplot(2, 2, 2)
    plt.hist(gray.ravel(), 256, [0, 256], color='black')
    plt.title('Original Histogram')

    # Apply histogram equalization
    equalized = cv2.equalizeHist(gray)

    plt.subplot(2, 2, 3)
    plt.imshow(equalized, cmap='gray')
    plt.title('Enhanced Grayscale Image')
    plt.axis('off')

    plt.subplot(2, 2, 4)
    plt.hist(equalized.ravel(), 256, [0, 256], color='black')
    plt.title('Enhanced Histogram')

    plt.tight_layout()
    plt.show()
```
## Colour Image Histogram Equalization
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the color image
img = cv2.imread("parrot.jpg")

if img is None:
    print("Error: parrot.jpg not found!")
else:
    # Split B, G, R channels
    b, g, r = cv2.split(img)

    # Convert BGR to HSV
    hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

    # Split H, S, V channels
    h, s, v = cv2.split(hsv)

    # Apply histogram equalization to V channel
    v_eq = cv2.equalizeHist(v)

    # Merge HSV channels
    hsv_eq = cv2.merge((h, s, v_eq))

    # Convert HSV back to BGR
    enhanced = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)

    # Display images and histograms
    plt.figure(figsize=(12, 8))

    # Original color image
    plt.subplot(2, 2, 1)
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title("Original Color Image")
    plt.axis("off")

    # Original B, G, R histograms
    plt.subplot(2, 2, 2)
    plt.hist(b.ravel(), 256, [0, 256],
             color="blue", alpha=0.5, label="Blue")
    plt.hist(g.ravel(), 256, [0, 256],
             color="green", alpha=0.5, label="Green")
    plt.hist(r.ravel(), 256, [0, 256],
             color="red", alpha=0.5, label="Red")
    plt.title("Original BGR Histograms")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")
    plt.legend()

    # Enhanced color image
    plt.subplot(2, 2, 3)
    plt.imshow(cv2.cvtColor(enhanced, cv2.COLOR_BGR2RGB))
    plt.title("Enhanced Color Image")
    plt.axis("off")

    # Enhanced V channel histogram
    plt.subplot(2, 2, 4)
    plt.hist(v_eq.ravel(), 256, [0, 256], color="purple")
    plt.title("Enhanced V Channel Histogram")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")

    plt.tight_layout()
    plt.show()

    # Save enhanced image
    cv2.imwrite("enhanced_color.jpg", enhanced)

    print("Color histogram equalization completed successfully!")
    print("Saved as enhanced_color.jpg")
```

##  Output




### Grayscale Histogram Equalization
<img width="1887" height="982" alt="image" src="https://github.com/user-attachments/assets/44550056-c121-446d-b3b1-1d3617c76a1e" />


- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization
<img width="1877" height="955" alt="image" src="https://github.com/user-attachments/assets/ca331eb0-f8df-470f-b892-52a51df592f3" />

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
