# 🧠 Logo Clustering using Unsupervised Learning & Feature Similarity Graphs

This project focuses on clustering **logos** using various unsupervised learning techniques and a custom similarity graph approach without traditional ML clustering algorithms. The core idea is to extract meaningful image features and group visually similar logos together.

---

## 📁 Dataset

All logo images are stored in the `dataset/logos/` directory. Images are preprocessed (resized) before feature extraction to ensure uniformity.

---

## 🧪 Methods Used

### 1. **GMM with SIFT**
- **Features**: SIFT descriptors (mean-pooled)
- **Clustering**: Gaussian Mixture Model (GMM)
- **Goal**: Cluster logos based on local keypoints and descriptors.

---

### 2. **GMM with SIFT + HOG**
- **Features**: SIFT (mean-pooled) + Histogram of Oriented Gradients
- **Clustering**: Gaussian Mixture Model (GMM)
- **Goal**: Combine shape and texture for richer representation.

---

### 3. **DBSCAN with SIFT + HOG**
- **Features**: Concatenated SIFT + HOG features
- **Clustering**: DBSCAN (density-based)
- **Goal**: Discover arbitrary-shaped clusters without specifying cluster count.

---

### 4. **KMeans with ResNet (Pretrained CNN)**
- **Features**: Deep features extracted from a pretrained ResNet model (e.g., `resnet50`)
- **Clustering**: KMeans
- **Goal**: Use semantic features from a deep neural network for higher-level clustering.

---

## 🛠 Custom Non-ML Approach (No KMeans / DBSCAN / GMM)

### ✅ **Feature Extraction**
- **SIFT** (scale/structure)
- **HOG** (edges/orientation)
- **HSV Histogram** (color)
- Features are **concatenated** and **L2-normalized**.

### ✅ **Similarity Graph**
- Cosine similarity is computed pairwise between image feature vectors.
- A **graph** is built where images are connected if their similarity > threshold (e.g., 0.9).

### ✅ **Clustering via DFS**
- The similarity graph is traversed using **Depth-First Search (DFS)**.
- **Connected components** in the graph are treated as clusters of similar logos.

### 🔍 Benefits
- Interpretable, non-ML approach
- Fine-grained control via similarity threshold
- Useful when number of clusters is unknown or difficult to estimate

---

## 📊 Outputs

Each method outputs cluster assignments by image filename. Cluster quality can be evaluated qualitatively by visual inspection or by silhouette scores (for ML methods).

---

