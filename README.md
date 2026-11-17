# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Program : 

```
# Edge Detection using OpenCV
# Sobel, Prewitt, Roberts, Laplacian and Canny

# Step 1: Import Libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load Image
img = cv2.imread('tree.jpeg')

if img is None:
    print("Error: Image not found!")
else:
    print("Image loaded successfully!")

    # Step 3: Convert Image to Grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 4: Sobel Edge Detection
    sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
    sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

    sobel = cv2.magnitude(sobel_x, sobel_y)
    sobel = cv2.convertScaleAbs(sobel)

    # Step 5: Prewitt Edge Detection
    kernel_x = np.array([[-1, 0, 1],
                         [-1, 0, 1],
                         [-1, 0, 1]])

    kernel_y = np.array([[-1, -1, -1],
                         [ 0,  0,  0],
                         [ 1,  1,  1]])

    prewitt_x = cv2.filter2D(gray, cv2.CV_32F, kernel_x)
    prewitt_y = cv2.filter2D(gray, cv2.CV_32F, kernel_y)

    prewitt = cv2.magnitude(prewitt_x, prewitt_y)
    prewitt = cv2.convertScaleAbs(prewitt)

    # Step 6: Roberts Edge Detection
    kernel_x = np.array([[1, 0],
                         [0, -1]])

    kernel_y = np.array([[0, 1],
                         [-1, 0]])

    roberts_x = cv2.filter2D(gray, cv2.CV_32F, kernel_x)
    roberts_y = cv2.filter2D(gray, cv2.CV_32F, kernel_y)

    roberts = cv2.magnitude(roberts_x, roberts_y)
    roberts = cv2.convertScaleAbs(roberts)

    # Step 7: Laplacian Edge Detection
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    # Step 8: Canny Edge Detection
    canny = cv2.Canny(gray, 100, 200)

    # Step 9: Display All Edge Detection Results
    images = [sobel, prewitt, roberts, laplacian, canny]

    titles = ['Sobel', 'Prewitt', 'Roberts',
              'Laplacian', 'Canny']

    plt.figure(figsize=(15, 10))

    for i in range(5):
        plt.subplot(2, 3, i + 1)
        plt.imshow(images[i], cmap='gray')
        plt.title(titles[i])
        plt.axis('off')

    plt.tight_layout()
    plt.show()

    # Step 10: Display Original Image
    plt.figure(figsize=(6, 6))
    plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.title('Original Image')
    plt.axis('off')
    plt.show()

```

## Developed By

- **Name:**  Santhosh K
- **Register No:** 212225040379

---

## Output

<img width="280" height="411" alt="image" src="https://github.com/user-attachments/assets/eddb3d28-20fd-4a95-a44b-05a22c364251" />



###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map

  <img width="280" height="411" alt="image" src="https://github.com/user-attachments/assets/afeeaa70-5eaf-48fd-ad4c-057273efc444" />
 

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges

  <img width="280" height="411" alt="image" src="https://github.com/user-attachments/assets/47deffa5-801c-43a1-b227-53d774151140" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise

  <img width="280" height="411" alt="image" src="https://github.com/user-attachments/assets/63f28191-c78c-4f93-aef7-3d4d04c4b5b7" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

<img width="280" height="411" alt="image" src="https://github.com/user-attachments/assets/4a60f489-4f3d-4322-9b77-8961e0e7b9d0" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
