# Cartoonification-of-Image using-K-means-and-SVD
Our goal is to convert ordinary images into captivating cartoons, and to achieve this, we plan to develop a Python application utilizing OpenCV. The application will employ machine learning algorithms, specifically K-means Clustering and Singular Value Decomposition, in conjunction with a Bilateral Filter. 


BACKGROUND STUDY

The process of creating a cartoon effect of an image can be initially branched into 2 divisions – 

1.	Reduction of colour palette
2.	Highlighted Edges

REDUCTION OF COLOR PALETTE

The primary objective is to minimize colour variations and incorporate cartoon features. This involves utilizing multiple filters to reduce colours and achieve uniform colour regions.

1.	BILATERAL FILTERING: 
This filter plays a crucial role in smoothing images while preserving edges and eliminating noise. The process involves reading an image file, storing it in a matrix object, creating an empty matrix for results, and applying a bilateral filter. The characteristics of the filter depend on the kernel size, and testing is carried out through multiple iterations.

2.	GAUSSIAN BLUR: 
Widely employed in image processing, Gaussian Blur is an effect used to diminish image noise and minimize details. This smoothing technique serves as an initial step in computer vision algorithms, aiming to enhance image structures at various scales.

HIGHLIGHTED EDGES

Achieving a smooth outline that accurately represents or encloses the shape of an image is a crucial element for obtaining a high-quality image. The edge processing tasks employed in this context encompass:

1.	MEDIAN BLUR:
To smooth the image, a blurring effect is applied through the Median Blur() function. This involves assigning a mean value to the center pixel, calculated as the mean of all pixels within the kernel. Additionally, it aids in noise removal from the image.

2.	ADAPTIVE THRESHOLD:
This step focuses on retrieving and highlighting edges using adaptive thresholding. The threshold value is determined as the mean value of surrounding pixel values within a single block, subtracting a constant 'c'. 'c' represents the constant subtracted from the mean of surrounding neighbourhood pixels.

The final step involves combining the reduced colour palette and the highlighted edges image through masking. This is achieved by performing bitwise operations on the highlighted edges and the smooth colours, resulting in the creation of a cartoon image.

ALGORITHM

K-MEANS CLUSTERING

K-means clustering stands as a key algorithm supported by unsupervised machine learning. 

Before delving into the intricacies of K-means, it's essential to grasp the fundamentals of unsupervised learning.

Unlike its supervised counterpart, unsupervised learning lacks predefined labels, steering away from predictions and focusing on creating clusters or groups. This segmentation is based on the features provided to the model, allowing the data to be organized without predefined expectations.

In the context of unsupervised learning, K-means clustering doesn't predict outcomes but rather divides the data into distinct clusters. The algorithm follows a set of mathematical steps:

Step 1: 
Determine the number of clusters, employing methods like the elbow method or domain knowledge for appropriate selection.

Step 2: 
Randomly assign K points, also known as centroids, from the dataset.

 

Step 3: 
Adjust each K point towards its nearest centroid in the final step, forming cohesive clusters or groups.

 


SINGULAR VALUE DECOMPOSITION (SVD)

Singular Value Decomposition (SVD) is an important technique in unsupervised machine learning, much like K-means clustering. Before delving into the details of SVD, it's crucial to understand the broader context of unsupervised learning. In unsupervised learning, there are no predefined labels, and the focus is on uncovering patterns and structures within the data.

Similarly, in the case of SVD, rather than making predictions, the objective is to decompose a matrix into three other matrices, revealing underlying patterns and relationships within the data. This process aids in dimensionality reduction and feature extraction.

The steps involved in the SVD approach are as follows:

1.	Decomposition:
Choose a matrix and decompose it into three matrices - U, Σ, and V^T. Here, U represents left singular vectors, Σ is a diagonal matrix of singular values, and V^T denotes the transpose of right singular vectors.

2.	Dimensionality Reduction:
The singular values in Σ help identify the importance of each feature or component. By selecting the top singular values, one can reduce the dimensionality of the data while retaining essential information.

3.	Representation:
The three matrices obtained from decomposition can be used to represent the original matrix. This representation is often more compact, focusing on the most significant features.

Just like K-means clustering, SVD in unsupervised learning allows for a deeper understanding of data patterns without the need for predefined labels. It is a valuable tool for extracting meaningful information and reducing the complexity of high-dimensional data.

Approach:

1.	Reading the Image:
The code reads a grayscale image using OpenCV from a specified file path. The image is stored in the variable `img`.

2.	Singular Value Decomposition (SVD):
SVD is applied to the image, decomposing it into three matrices: U (left singular vectors), S (singular values), and Vt (right singular vectors).

3.	Reducing Dimensionality:
The code retains only the first `k` singular values, setting the rest to zero. This step helps in reducing the dimensionality of the image.

4.	Image Reconstruction:
The image is reconstructed using the modified singular values and the original singular vectors. The result is stored in `img_svd`.

5.	Normalization:
The reconstructed image values are normalized to the range [0, 255] and converted to unsigned 8-bit integers to prepare it for display.

6.	Bilateral Filtering:
A bilateral filter is applied to the cartoonified image (`img_svd`) for smoothing. The parameters `d`, `sigmaColor`, and `sigmaSpace` control the diameter of each pixel neighbourhood, colour smoothing, and spatial smoothing, respectively.

7.	Display:
The code then displays three images side by side using Matplotlib:
a)	The original grayscale image.
b)	The cartoonified image obtained through SVD.
c)	The smoothed version of the cartoonified image.

8.	Mounting Google Drive:
The code mounts Google Drive to access the image file specified by the path.

9.	Image Path and Function Call:
The correct image path is specified, and the `cartoonify_with_svd` function is called with the chosen image and a parameter `k` set to 50 (number of retained singular values).

In summary, this code leverages SVD for dimensionality reduction and then applies bilateral filtering to create a cartoon-like effect. The resulting images are displayed for visual comparison.


 
Considerations:
If your goal is to emphasize global structure and smooth transitions, SVD may be more suitable.
If you want to create a cartoon effect with well-defined color regions and sharp transitions, K-means clustering might be a better choice.


APPLICATIONS AND END RESULT:
The following are the objectives of the result obtained by us:

❖	To create a rapid image processing technique with high detection rates.

❖	To provide a high-accuracy model which is precise as compared to current existing models.

❖	To provide a possibly low false positive rate.

CONCLUSION


Reduction of colour palette and highlighted edges are two common problems in cartooning images. This paper proposes an efficient method for cartooning images. The test results by using the proposed method of cartooning will show that the developed method could possibly extract meaningful cartoon objects well in different characters and backgrounds. The cartoon objects that are extracted are expected to be effectively used in cartoon image retrieval because they surely are able to represent the colour characteristics of cartoon objects well. The result of the experiment shows we get a precise cartoon image by using bilateral filter and adaptive threshold methods with complete removal of noise and retention of clear edges from the original images. In short, this method could be the most reliable method for cartooning images.
