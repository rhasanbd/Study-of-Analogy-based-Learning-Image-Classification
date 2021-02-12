# Study of Analogy based Learning - Image Classification


In this notebook, we investigate the following question:

- Do the distance-based metrics (e.g., Minkowski) provide a reliable measure of similarity between the images of the same class and different classes? 

The **analogy based** learning models such as K-Nearest Neighbors (K-NN) use distance similarity metric to classify images. Image pixels are considered as features. Two images are "similar" (share the same semantic identity or class label) if their pixel-wise Minkowski distance is small. Using the **Euclidean distance** metric as a measure of similarity, we compare the intra-class and inter-class distances. We show that:

- The distance-based metrics (e.g., Minkowski) are not effective, when applied at pixel level, for determining similarity between the images. The inter-class distance is not necessarily and always larger/different from the intra-class distance. It depends on the dataset.



## Tasks

Our similarity analysis study is performed via three tasks.

- Task 1: Compute Inter-class & Intra-class Euclidean Distance

- Task 2: Compute the Euclidean Distance between an Image and Its Augmented Versions

- Task 3: Visual Similarity Analysis by Projecting the Images on a 2D Space


## Dataset

For this analysis, we use two popular Machine Learning (ML) image datasets: MNIST handwritten digits & CIFAR-10.

- While the images of the MNIST dataset are "normalized" (centered and similar background), the images of the CIFAR-10 dataset has a lot of variations.


### MNIST

The MNIST (Modified National Institute of Standards and Technology) dataset contains 70,000 small images of digits handwritten by high school students and employees of the US Census Bureau. Each image is labeled with the digit it represents.

Each image is grayscale 28 x 28 pixels, and each feature simply represents one pixel’s intensity, from 0 (white) to 255 (black).


### CIFAR-10
The CIFAR-10 (Canadian Institute For Advanced Research) dataset contains 60,000 images of 10 different classes: airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks. 

Each image is color with 32 x 32 x 3 pixels. 


## Summary of Observations


- In the MNIST dataset, there exists a global pattern in the pixel distribution of the same digit across all images of its category. The MNIST data is relatively clean. Digits are preprocessed by normalizing the size and centered in a fixed-size image. On the other hand, we observe a lot of variatiosn in the CIFAR-10 images of the same object. 

- The background pixels in the MNIST images follow a silimar pattern in all images belonging to the same class. However, in CIFAR-10 images, there are a lot of variations in the background pixels across the images of the same object.

- In the MNIST dataset, the intra-class distance is generally smaller than the inter-class distance. However, this is not true in the CIFAR-10 dataset.




- In MNIST, the pixel-level similarity is good enough to determine the semantic identity of the images. This is due to the fact that MNIST images have a strong bias. This bias is manifested as follows.

        -- Images are centered

        -- Less variation in the distribution of the pixels of the same class

        -- Share the same background

- However, the CIFAR-10 images don't have this bias. As a consequence, pixel level analogy does not lend useful to determine the semantic idetity.



## Beyond Raw Pixel Based Similarity: Is Analogy based Learning Effective for Image Classification?

The distance metric does not provide a reliable measure, when applied at the pixel level, to determine semantic identity of an image. It doesn't mean that the distance based technique or analogy based reasoning in general is flawed/weak. The similarity based approach is effective when more expressive and powerful high-level features are extracted from raw pixels. In other words, while distance measures at the raw pixel level produce spurious results, similarity calculation on the high-level features reveal semantic identity.

The following papers achieve state-of-the-art results on image classification by applying the K-NN analogy based approach on the learned features.

- Xu et al. (2020) Hierarchical Semantic Aggregation for Contrastive Representation Learning https://arxiv.org/pdf/2012.02733v1.pdf

- Caron et el. (2021) Unsupervised Learning of Visual Features by Contrasting Cluster Assignments https://arxiv.org/pdf/2006.09882.pdf
