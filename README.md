# Experiment 07 -- Hough Transform

## Name : SURYA D
## RegNo : 212224220115

## Aim

To detect straight lines in an input image using the Hough Transform
technique with OpenCV.

## Procedure

1.  Import the required libraries: OpenCV (`cv2`), NumPy, and
    Matplotlib.
2.  Load the input image `my.jpeg` using `cv2.imread()`.
3.  Convert the input image from BGR to grayscale using
    `cv2.cvtColor()`.
4.  Display the original input image and the grayscale image.
5.  Apply the Canny edge detector using `cv2.Canny()` with threshold
    values of 50 and 150.
6.  Display the detected edges.
7.  Apply the Probabilistic Hough Line Transform using
    `cv2.HoughLinesP()` with the following parameters:
    -   Distance resolution: 1 pixel
    -   Angular resolution: 1 degree (`np.pi / 180`)
    -   Threshold: 100
    -   Minimum line length: 50 pixels
    -   Maximum line gap: 10 pixels
8.  If lines are detected, draw them on the input image in green with a
    thickness of 2 pixels.
9.  Display the final image containing the detected lines.

## Program

``` python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the image
image = cv2.imread('my.jpeg')

# Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display the input image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')

# Display the grayscale image
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Detect edges using the Canny operator
edges = cv2.Canny(gray_image, 50, 150)

# Display the Canny edge detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Detect line coordinates using the Probabilistic Hough Transform
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)

# Draw the detected lines on the image
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)

# Display the result of the Hough Transform
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```

## Output

  **Input Image:** The original image loaded from `my.jpeg`.

<img width="203" height="410" alt="download" src="https://github.com/user-attachments/assets/bcdb5abe-4206-4b72-b3b2-9fe3aa28fab2" />

 **Grayscale Image:** The input image converted into grayscale.

<img width="203" height="410" alt="download" src="https://github.com/user-attachments/assets/be28e5d2-cdb0-485e-983e-cfb9dc85ceef" />


 **Canny Edge Detector:** The edges detected from the grayscale
    image.

<img width="203" height="410" alt="download" src="https://github.com/user-attachments/assets/45748ffa-eeb7-4f2b-af22-c5993f26be0a" />


 **Result of Hough Transform:** The final image with the detected
    straight lines drawn in green.

<img width="244" height="410" alt="download" src="https://github.com/user-attachments/assets/bb2393ed-4e70-477b-a640-46d9a056123e" />


## Result

Thus, straight lines in the input image were detected successfully using
the Probabilistic Hough Transform in OpenCV, and the detected lines were
drawn on the original image.
