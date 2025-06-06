# Face Recognition Using Principal Component Analysis (PCA)

This project implements a face recognition system leveraging Principal Component Analysis (PCA) to efficiently identify individuals. The system is developed using MATLAB and utilizes the Face94 dataset.

## Project Abstract

The increasing demand for secure and efficient identity verification has driven advancements in face recognition technologies. This project addresses this demand by employing Principal Component Analysis (PCA) for face recognition, specifically using the Face94 dataset within MATLAB to create a robust, data-driven recognition system.

PCA is particularly well-suited for this task due to its ability to reduce the dimensionality of high-resolution facial images, isolating essential features (referred to as "eigenfaces") that distinguish individual faces. This approach facilitates efficient matching based on similarity, demonstrating PCA's effectiveness in delivering accurate recognition outcomes. The project highlights PCA's potential applications in security, authentication, and human-computer interaction systems.

## Understanding PCA

Principal Component Analysis (PCA) is a dimensionality reduction technique used to decrease the number of features (or dimensions) in a dataset while retaining as much variability as possible. It transforms the original data into a new set of variables called principal components, which are uncorrelated and ordered by the amount of variance they capture. PCA aims to retain as much variance as possible while reducing the number of features in the dataset.

## Dataset: Face94

The project utilizes the Face94 dataset, which includes:

* **Subjects:** 30 individuals
* **Training Set:** 10 images per person, totaling 300 images
* **Original Image Size:** 100 x 90 pixels
* **Initial Vector Size:** 1 x 36000
* **Resized Image:** 90 x 100 pixels
* **Resized Vector Size:** 1 x 9000
* **Testing Set:** 10 images per person, totaling 300 images

## Preprocessing Steps

1.  **Image Loading and Resizing:** Face94 images are loaded into MATLAB and resized to a consistent resolution, typically 100x90 pixels.
2.  **Flattening Images:** Each 2D face image is converted into a 1D vector (flattened array). This creates a data matrix `X` where each row represents an image, and each column represents pixel values.

## Data Matrix

The input data is organized into a matrix where each row represents an observation (e.g., an image) and each column represents a feature (e.g., pixel values). Once images are flattened, a data matrix `X` is constructed where each column represents the flattened face image vectors.

## Mean Image and Mean Centering

1.  **Mean Image Definition:** The mean image is computed by averaging the pixel values across all images in the dataset. This single image represents the central tendency of the pixel values in the dataset.
2.  **Centering the Data:** The data is centered by subtracting the mean image from each individual image in the dataset. This process ensures that the resulting data has a mean of zero, which is crucial for accurate variance analysis.

## Covariance and Covariance Matrix

1.  **Covariance Definition:** Covariance measures how two variables vary together. If two features tend to increase and decrease together, they have positive covariance. If one tends to increase when the other decreases, they have negative covariance.
2.  **Covariance Matrix in PCA:** The covariance matrix generalizes this concept across multiple features. For a dataset with multiple features (e.g., pixels in an image), it shows the covariance between every possible pair of features.
3.  **Covariance Matrix Calculation:** Given a data matrix `X` with `n` rows (observations) and `d` columns (features), the covariance matrix `Q` will be of size `d x d`, calculated as: $Q = X^T X / (n-1)$.

## Structure of the Covariance Matrix

* **Diagonal Elements:** The diagonal elements represent the variance of each feature, indicating how much each individual feature varies on its own.
* **Off-Diagonal Elements:** The off-diagonal elements represent the covariance between pairs of features, showing how they vary together.
* **Importance in Image Processing:** In image processing, the covariance matrix captures relationships between pixel values across images. High covariance between neighboring pixels often indicates similar values, which helps PCA determine the principal components that represent the most significant patterns in the data.

## Eigenvalues and Eigenvectors

* **Eigenvalues:** Eigenvalues represent the amount of variance captured by each principal component. A larger eigenvalue indicates that the corresponding eigenvector (principal component) captures more information about the data.
* **Eigenvectors:** Eigenvectors are the directions in the feature space along which the variance is maximized. Each eigenvector corresponds to a principal component.
* **Sorting:** After obtaining the eigenvalues and eigenvectors, they are sorted in descending order. This step allows for identification of which principal components explain the most variance in the data.

## Selecting Principal Components and Projecting Data

1.  **Selecting Principal Components:** Once the eigenvalues and eigenvectors are sorted, the top `k` eigenvectors (those corresponding to the largest eigenvalues) are chosen to form a new feature space. These selected eigenvectors are the new axes (principal components) for the transformed space.
2.  **Projecting Data into PCA Space:** The original data is then projected onto the new feature space formed by the principal components. This step transforms the original images into a lower-dimensional space while preserving as much variance as possible.

## Reference

1.  Turk, M., & Pentland, A. (1991). "Face recognition using eigenfaces." Proceedings of the IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR).