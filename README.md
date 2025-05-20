# OPENING--AND-CLOSING
## Aim
To implement Opening and Closing using Python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV
## Algorithm:
### Step1:
Create a white image of specified size and add black text to it using cv2.putText.

### Step2:
Add random salt-and-pepper noise to the image by setting random pixels to black or white.

### Step3:
Create a smaller structuring element (kernel) of size 5x5 using np.ones().

### Step4:
Apply the Opening operation using cv2.morphologyEx() with erosion followed by dilation.

### Step5:
Apply the Closing operation using cv2.morphologyEx() with dilation followed by erosion.

## Program:

``` Python
# Import the necessary packages
import cv2
import numpy as np
from matplotlib import pyplot as plt

# Create the Text using cv2.putText
img = np.ones((300, 600), dtype="uint8") * 255  
cv2.putText(img, 'SARISHA', (160, 150), cv2.FONT_HERSHEY_SIMPLEX, 3, (0, 0, 0), 5)  
noise = np.random.rand(*img.shape)
img[noise < 0.05] = 0  
img[noise > 0.95] = 255  
kernel = np.ones((5, 5), np.uint8)  
opening = cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)
closing = cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)
plt.figure(figsize=(12, 8))


# Create the structuring element
plt.subplot(2, 3, 2)
plt.title('Original Image with Noise')
plt.imshow(img, cmap='gray')
plt.axis('off')


# Use Opening operation
plt.subplot(1, 3, 2)
plt.title('Opening Operation')
plt.imshow(opening, cmap='gray')
plt.axis('off')

# Use Closing Operation
plt.subplot(1, 3, 3)
plt.title('Closing Operation')
plt.imshow(closing, cmap='gray')
plt.axis('off')
plt.show()

```
## Output:

### Display the input Image
![image](https://github.com/user-attachments/assets/9b98cffb-9b51-4eff-98dd-50569283b774)


### Display the result of Opening
![image](https://github.com/user-attachments/assets/738da111-06a4-4a48-af18-4d0497a9e884)


### Display the result of Closing
![image](https://github.com/user-attachments/assets/1f923f10-2563-429c-9545-820aa6cfbeaf)


## Result
Thus the Opening and Closing operation is used in the image using python and OpenCV.
