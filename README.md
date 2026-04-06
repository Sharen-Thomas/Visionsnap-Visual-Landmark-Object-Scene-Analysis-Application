# Visionsnap-Visual-Landmark-Object-Scene-Analysis-Application

## OVERVIEW

A computer vision application built with OpenCV that analyzes and understands images of Dubai's urban environment. Detects landmarks (Burj Khalifa, Burj Al Arab, Palm Jumeirah), faces with mood estimation, classifies time-of-day, assesses image quality, and finds similar images, all through an intuitive GUI.

## WHAT IT DOES

### LANDMARK DETECTION
- HAAR Cascade + ORB detection for Burj Khalifa, Burj Al Arab, Palm Jumeirah

### FACE DETECTION 
- Detects faces, eyes, smiles with mood estimation (Happy/Neutral)

### TIME-OF-DAY CLASSIFICATION
- Grayscale intensity analysis → Day/Night classification

### IMAGE QUALITY ASSESSMENT 
- Brightness, contrast, sharpness metrics with enhancement suggestions

### SIMILARITY RETRIEVAL 
- HSV histogram + edge detection to find top 3 similar images

### ANNOTATION TOOL
- Rectangle, circle, line, freehand drawing with color selection

### BATCH PROCESSING 
- Process entire folders with automatic sorting into Day/Night/Error folders

## KEY RESULTS

### DETECTION PERFORMANCE 

#### BURJ KHALIFA
- Method: HAAR + ORB
- Notes: Custom bounding logic to merge multiple detections

#### BURJ AL ARAB
- Method: HAAR + ORB
- Notes: Fine-tuned scaleFactor=1.03, minNeighbors=2

#### PALM JUMEIRAH 
- Method: HAAR + ORB
- Notes: Custom logic to avoid over-detection

### QUALITY THRESHOLDS

#### BRIGHTNESS
- Threshold: < 60 = Too dark, > 190 = Too bright
- Interpretation: Overall lightness

#### CONTRAST
- Threshold: < 30 = Low contrast
- Interpretation: Light/dark difference

#### SHARPNESS
- Threshold: < 100 = Blurry
- Interpretation: Image clarity

### TIME-OF-DAY CLASSIFICATION

- Method: Grayscale pixel intensity analysis (not HSV or deep learning)
- Accuracy: Highest among tested approaches
- Output: Auto-sorts images into Day/Night/Error subfolders

## TECH STACK 

- Language: Python
- Computer Vision: OpenCV (HAAR Cascades, ORB, HSV histograms)
- GUI: Tkinter
- Image Processing:	NumPy, scikit-image
- Similarity Metrics:	Correlation, Chi-Square, Intersection, Bhattacharyya

## FEATURES IN DETAIL

1. Landmark Detection (HAAR + ORB Dual Strategy)
   - Loads custom-trained HAAR classifiers for each landmark
   - Falls back to ORB feature matching if HAAR fails
   - Custom bounding logic merges multiple detections into single accurate box

2. Face Detection + Mood Estimation
   - Detects faces → then eyes and smiles within face region
   - Smile detected → "Happy" & No smile → "Neutral"
   - Output: Blue boxes (faces), Green boxes (eyes), Red boxes (smiles)

3. Time-of-Day Classification
   - Converts to grayscale → analyzes pixel intensity distribution
   - Classifies as "Day" (bright pixels dominate) or "Night" (dark pixels dominate)
   - Batch mode auto-sorts into folders

4. Similarity Retrieval
   - Choose comparison method: Color (HSV histogram) or Edges (edge detection)
   - Returns top 3 most similar images with similarity scores

5. Image Quality Assessment
   - Calculates brightness (mean pixel), contrast (std dev), sharpness (Laplacian variance)
   - Provides pass/fail feedback and enhancement suggestions
   - Displays RGB histogram

6. Annotation Tools
   - Draw rectangles, circles, lines, freehand
   - Color picker + line thickness control
   - Save annotations without overwriting originals

## FILES 

- 'CSCI435_Project_Report.pdf' - Complete project documentation

## DISCLAIMER
**This repository is for viewing purposes only. It is not licensed for copying, modification, or commercial use without explicit permission from the author.**
