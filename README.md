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
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('rose.jpg', cv2.IMREAD_GRAYSCALE)

plt.imshow(img, cmap='gray')
plt.title('Original Rose Image')
plt.axis('off')
plt.show()
```
### Step 2:
Read the image `parrot.jpg` in grayscale format.
```
plt.hist(img.ravel(), 256, range=[0,256])
plt.title('Original Image Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

```

### Step 3:
Display the grayscale image and plot its histogram.
```
img_eq = cv2.equalizeHist(img)
```
### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.
```
plt.hist(img_eq.ravel(), 256, range=[0,256])
plt.title('Equalized Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()
```

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

### Developed By:
**Name:** DHARSHINI V

### Register No:
212225040184

---

##  Output

<img width="761" height="507" alt="628221148-e988ad81-5246-49e2-a032-df915011a3a3" src="https://github.com/user-attachments/assets/ca4ee282-85e5-491d-92f0-c4f98e6b4359" />


<img width="770" height="562" alt="628221777-2a9fcc3c-f4f8-4969-96f8-4e01dc3dc7a6" src="https://github.com/user-attachments/assets/404681d2-3e02-41e7-a0f8-81803c1ce757" />


<img width="837" height="627" alt="628221902-8f6482dd-462b-4ed0-a8b8-072a8863a61f" src="https://github.com/user-attachments/assets/03e4081a-07de-4756-ab90-300cad560d35" />


<img width="781" height="495" alt="628222005-06bb8d76-6166-466f-864d-ef49a4de453e" src="https://github.com/user-attachments/assets/8a5f9479-fbd5-4c5f-9108-98e3ce115d16" />


<img width="746" height="346" alt="628222250-52760947-17c9-423a-9316-69d6f34879c0" src="https://github.com/user-attachments/assets/dfb678ad-73d5-4d0f-9851-ab0f84bcd1ff" />


<img width="881" height="791" alt="628222453-9fa82cd4-d3ce-4a19-8920-d2ebbab0c817" src="https://github.com/user-attachments/assets/a42573c1-2b6e-48ef-a76d-da4f8791de33" />




### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
