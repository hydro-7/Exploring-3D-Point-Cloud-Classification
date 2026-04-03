# 3D Point Cloud Classification and Segmentation

Here is an overview of the 5 architectures used in this repository.

## 1. DGCNN Classification
Dynamic Graph Convolutional Neural Network introduces a novel operation called EdgeConv.
This mechanism constructs a local neighborhood graph dynamically at each layer of the network.
Rather than relying on fixed spatial relationships, it recalculates point proximities in the feature space.
This allows the model to capture geometric features and semantic relationships effectively.
By grouping points that share similar features, it understands complex topological structures.
The architecture is highly robust to variations in point density across the cloud.
It excels at global classification tasks by aggregating local features into a comprehensive global descriptor.
This paradigm shift makes it a powerful tool for analyzing unordered point sets.

## 2. PointCNN Classification
PointCNN tackles the challenge of unordered point clouds through a unique mathematical transformation.
It utilizes a learnable X transformation to weight and permute the input points and their features.
This process effectively projects the unordered points into a latent space where standard convolutions apply.
The architecture extracts local features from neighborhoods defined by K nearest neighbors.
By sorting the points into a canonical order, it preserves spatial correlations perfectly.
This design bridges the gap between grid based images and irregular point clouds.
It performs exceptionally well on complex classification datasets with varying geometries.
The method offers a pathway to apply traditional convolutional logic to 3D spaces.

## 3. PointNet Classification
PointNet is the pioneering architecture that processes point clouds directly without converting them to voxels.
It treats each point individually and passes them through a shared multilayer perceptron network.
This independent processing ensures that the model remains highly efficient and computationally lightweight.
To achieve permutation invariance, it utilizes a symmetric max pooling function at the end.
This pooling operation collapses all individual point features into a single global feature vector.
It captures the essential skeleton of the 3D shape while ignoring local structural interactions early on.
PointNet serves as the fundamental baseline for modern 3D deep learning architectures.
Its simple yet effective design handles the unstructured nature of point clouds flawlessly.

## 4. PointConv Segmentation
PointConv is designed to perform dense prediction tasks like segmentation on continuous probability distributions.
It computes the weights of convolutions as a continuous function of the 3D coordinates.
To compensate for uneven point densities, it incorporates a learned inverse density scale.
This scaling ensures that densely populated regions do not dominate the feature extraction process.
The model effectively translates traditional image convolution into the continuous 3D domain.
It utilizes an encoder and decoder structure to capture both local details and global context.
By propagating features back to the original resolution, it assigns a specific class to every single point.
It represents a mathematically elegant solution to irregular data segmentation.

## 5. PointNet2 Segmentation
PointNet2 expands upon the original PointNet by introducing a hierarchical structure to capture local details.
It groups points into overlapping local regions using farthest point sampling and ball queries.
Each of these local regions is then processed by a miniature PointNet module to extract contextual features.
This hierarchical downsampling allows the network to understand structures at multiple scales.
For segmentation, the model employs distance based feature interpolation to upscale the learned features.
Skip connections are used to fuse global and local features seamlessly and accurately.
This localized feature aggregation makes it significantly better at recognizing fine details.
It is exceptionally well suited for dense segmentation tasks in complex 3D environments.

## Final Metrics Table

<table>
  <tr>
    <th>Model</th>
    <th>oAcc</th>
    <th>mAcc</th>
    <th>mIoU</th>
  </tr>
  <tr>
    <td>DGCNN</td>
    <td>n</td>
    <td>n</td>
    <td>Not Applicable</td>
  </tr>
  <tr>
    <td>PointCNN</td>
    <td>n</td>
    <td>n</td>
    <td>Not Applicable</td>
  </tr>
  <tr>
    <td>PointNet</td>
    <td>n</td>
    <td>n</td>
    <td>Not Applicable</td>
  </tr>
  <tr>
    <td>PointConv</td>
    <td>n</td>
    <td>n</td>
    <td>n</td>
  </tr>
  <tr>
    <td>PointNet2</td>
    <td>n</td>
    <td>n</td>
    <td>n</td>
  </tr>
</table>
