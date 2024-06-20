# Interactive Foreground Segmentation Using K-Means Clustering

## Introduction

The task of image segmentation is a fundamental operation in the field of computer vision, with applications ranging from medical imaging to autonomous vehicles. The goal of segmentation is to partition an image into segments, or sets of pixels, that correspond to different objects or regions of interest. Our approach introduces a semi-automatic segmentation method known as "Interactive Foreground Segmentation", which incorporates user input in the form of seed points to improve the precision of the segmentation task.

## Methodology

### Data Preprocessing

The original and auxiliary images were preprocessed with the following steps:

- **Gaussian Blur**: Applied to the original and auxiliary images to reduce noise and facilitate more accurate seed extraction.
- **HSV Conversion**: The auxiliary images were converted from BGR to HSV color space to more reliably detect the seed pixels marked by the user.

### Seed Pixel Extraction

Seed pixels for the foreground and background were extracted using predefined color thresholds in the HSV space. These seeds were utilized as initial data points for the K-Means clustering algorithm.

### K-Means Clustering

K-Means was implemented from scratch, consisting of the following steps:

1. **Initialization**: Centroids were initialized using random seed pixels from the dataset.
2. **Assignment**: Each pixel was assigned to the nearest centroid based on Euclidean distance.
3. **Update**: Centroids were recalculated as the mean of the assigned pixels. This process iterated until convergence or a maximum number of iterations was reached.

### Likelihood Computation

For each pixel in the image, a likelihood score was computed based on its distance from each centroid, using a non-squared exponential function to mitigate the downsides of small distance values.

### Post-Processing

After segmentation, the following post-processing steps were applied:

- **Morphological Operations**: Used to clean up the segmentation mask, closing holes and eliminating noise.
- **Connected Component Analysis**: Small, disconnected components likely to be noise were removed from the segmentation mask.
- **Contour Analysis**: Contours were used to fill in gaps within the segmented regions.

### Before 

- ![lady](https://github.com/MuhammadHaziq1337/Interactive-Foreground-Segmentation-Using-K-Means-Clustering/assets/148570176/e56b4f8e-78af-41a6-88cc-0d1e6c8fca40)
### After
- ![1-Lady-segmentation](https://github.com/MuhammadHaziq1337/Interactive-Foreground-Segmentation-Using-K-Means-Clustering/assets/148570176/f6bcf462-c0de-4d05-8a19-e6b785b4481c)


## Example Usage
- Open your terminal.
- Upload your image and seed points in the /data directory.
- Run the segmentation script:

## Dependencies
- NumPy
- OpenCV
- Matplotlib
