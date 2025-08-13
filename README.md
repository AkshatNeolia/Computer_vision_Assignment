# 🖼️ Computer Vision Assignment – Classical Filtering & Thresholding

**Author:** [AkshatNeolia](https://github.com/AkshatNeolia)  
**Objective:** Apply **classical filtering** and **thresholding techniques** (with a focus on Adaptive Gaussian Thresholding) to an image dataset using OpenCV.

---

## 📌 Overview
This project demonstrates **image preprocessing** and **segmentation** using:
- **Classical Filtering** – Smoothing and denoising images (mean, median, Gaussian blur).
- **Thresholding** – Converting grayscale images to binary for object-background separation.
- **Adaptive Gaussian Thresholding** – Localized thresholding for handling uneven illumination.

---

## 🔍 Techniques Used

### 1️⃣ Classical Filtering
- **Mean Filter:** Averages pixel values in a neighborhood.
- **Median Filter:** Replaces each pixel with the median of its neighbors (good for salt-and-pepper noise).
- **Gaussian Blur:** Weighted average using a Gaussian function.

**Pros:** Removes noise.  
**Cons:** May blur sharp edges.

---

### 2️⃣ Thresholding
- Converts grayscale → binary using a threshold value.  
- **Global Thresholding:** Single value for the whole image.  
- **Adaptive Thresholding:** Local pixel-based calculation.

---

### 3️⃣ Adaptive Gaussian Thresholding
- Calculates threshold per pixel using a **Gaussian-weighted sum** of neighboring pixels.
- **Advantages:**
  - Works well with uneven lighting.
  - Preserves edges and fine details.
  - Reduces background noise and shadows.

---

## 🛠️ Implementation

**Libraries Used:**
```python
import cv2
import matplotlib.pyplot as plt
import numpy as np
import glob
import os
```

**Steps:**
1. Load all `.jpg` images from the working directory.
2. Convert each image to grayscale.
3. Apply **Adaptive Gaussian Thresholding**:
   ```python
   th_img = cv2.adaptiveThreshold(img, 255,
                                  cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                  cv2.THRESH_BINARY,
                                  11, 2)
   ```
4. Save results to `thresholded_images/`.
5. Display **original** and **processed** images side-by-side.

---

## 📊 Results & Analysis
- **Success:** Foreground objects (e.g., butterfly) were clearly separated from the background despite lighting variations.
- **Strengths:** Strong edge preservation, detailed segmentation.
- **Limitations:** Small background noise speckles remain — can be reduced with **Gaussian blur** or **median filtering** before thresholding.

---

## 📂 Project Structure
```
📁 ComputerVision-Thresholding
│── 📜 Gaussian Threshold.py
│── 📜 README.md
```

---

## ▶️ How to Run
1. Place `.jpg` images in the working directory.
2. Run the script:
   ```bash
   python adaptive_gaussian_thresholding.py
   ```
3. Processed images will be saved in `thresholded_images/`.

---

## 📸 Sample Output

| Original Image | Adaptive Gaussian Threshold |
|---------------|-----------------------------|
| <img width="213" height="213" alt="{F82AEA86-C69A-4081-974D-A88D96069171}" src="https://github.com/user-attachments/assets/2b7fdb74-1075-478a-ba35-031c071a4119" /> | <img width="221" height="211" alt="{57BDD0C9-458A-4533-B73B-AB04F30DB94F}" src="https://github.com/user-attachments/assets/13fd506e-3754-4eb2-8857-e0850807b638" /> |

---

## 📜 License
This project is open-source and available under the **MIT License**.
