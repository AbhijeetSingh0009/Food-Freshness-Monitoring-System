# Food Quality Detection Using Deep Learning and Clustering

Final year undergraduate project focused on fruit quality detection using image preprocessing and data augmentation, along with clustering techniques such as K-Means, Agglomerative Clustering, and DBSCAN. Deep learning models were trained on clustered data to evaluate the impact of clustering on classification performance.

---
## About the Dataset
The Food Freshness Dataset is a labeled image collection designed for machine learning research in food quality classification. It includes images of fruits and vegetables categorized based on freshness levels, ranging from fresh to rotten. The dataset is a consolidated version of three publicly available datasets, enhanced through preprocessing and augmentation to ensure consistency and high-quality input for deep learning models.

All images are standardized to a resolution of 128×128 and normalized for model training. Additional preprocessing techniques such as grayscale conversion, edge detection, and brightness adjustment were applied to improve feature extraction. Labels were assigned based on visual inspection and clustering methods (K-Means and Agglomerative Clustering), capturing different stages of food quality. This dataset is suitable for developing computer vision models for spoilage detection, food safety applications, and intelligent inventory management systems.

![image](https://github.com/user-attachments/assets/bd42c6e1-fe22-460e-b0a2-b2c4ce8ab2f4)

This dataset is a curated and combined version of the following publicly available datasets on Kaggle:

[1] [Food Freshness by AlineSellwia](https://www.kaggle.com/datasets/alinesellwia/food-freshness)

[2] [Fresh and Stale Classification by swoyam2609](https://www.kaggle.com/datasets/swoyam2609/fresh-and-stale-classification)

[3] [Fruits and Vegetables Dataset by muhriddinmuxiddinov](https://www.kaggle.com/datasets/muhriddinmuxiddinov/fruits-and-vegetables-dataset)

Images from these sources were carefully selected and manually reviewed. The dataset was then processed to ensure consistency in image size, format, and quality. Transformations include resizing to 128x128, normalization, grayscale conversion, noise reduction, edge detection, and categorization based on freshness levels. Additionally, class balance was maintained, and augmentation techniques (flipping, rotation, brightness adjustments) were applied to increase variability and robustness of the dataset.

This finalized dataset serves as a comprehensive resource for food freshness classification tasks using machine learning and deep learning techniques.
---
## 📦 Dataset Details

- **Total Size**: 6.41 GB  
- **Total Classes**: 13  
- **Labels**: Fresh / Rotten  
- **File Types**: `.jpg`, `.jpeg`, `.png`  
- **Applications**: Image Classification, Freshness Detection, Computer Vision in Agriculture  
- **Dataset Link**: [4] [Finalized Datset](https://www.kaggle.com/datasets/ulnnproject/food-freshness-dataset)
---
## 📌 Usage

You can use this dataset for:

- Training deep learning models to detect fruit freshness
- Building mobile or web-based freshness detection tools
- Research in food quality monitoring using AI
---
## Model Architecture
![Model Architecture](https://github.com/user-attachments/assets/cf890e9f-35bc-4640-9710-1ab0f5f13f35)

## 📁 Dataset Preparation
The dataset contains fruit images labeled under the categories "Fresh" and "Rotten". The images were processed as follows:

### ✅ Data Preprocessing
- **Blurred** – Noise reduction using Gaussian blur.
- **Edge Detection** – Applied Canny edge detector.
- **Normalized** – Pixel values scaled between 0 and 1.
- **Original Image** – Base reference image.
- **Resized** – All images resized to **128 x 128**.
- **Grayscale** – Converted to grayscale for feature simplification.

### 🔄 Data Augmentation
- **Original Image**
- **Horizontal Flipping**
- **Rotation (±15°)**
- **Increased Brightness**
- **180° Rotation**

These augmentations helped to improve model generalization and prevent overfitting.

---

## 🔍 Clustering
Three clustering methods were used to label the data based on visual similarity:

### 1. K-Means Clustering
- **Clusters Chosen**: 5
- **Cluster Labels**:
  - `Cluster 0`: Fresh
  - `Cluster 1`: Slightly Aged
  - `Cluster 2`: Slate
  - `Cluster 3`: Spoiled
  - `Cluster 4`: Rotten

### 2. Agglomerative Clustering
- **Linkage Method**: Ward
- **Distance Metric**: Euclidean
- **Clusters Chosen**: 5 (Same as above)

### 3. DBSCAN
- Not used in final training due to inconsistent cluster sizes and undefined cluster count.

---

## 🧠 Model Training
Models were trained separately using data labeled with **K-Means** and **Agglomerative Clustering** results.

Each model was evaluated on four metrics:
- **Accuracy**
- **Precision (Macro Average)**
- **Recall (Macro Average)**
- **F1-Score (Macro Average)**

### 🏗️ Model Architectures Used
| Model | Architecture Summary |
|-------|----------------------|
| AlexNet | 5 Conv layers + 3 FC layers + ReLU + Dropout |
| DenseNet121 | Dense Blocks + Transition layers + Global Avg Pool + FC |
| InceptionV3 | Inception modules + Global Avg Pool + FC |
| MobileNetV2 | Depthwise separable convolutions + Bottleneck blocks |
| ResNet50 | Residual blocks with identity shortcut connections |
| VGG16 | 13 Conv layers + 3 FC layers |
| VGG19 | 16 Conv layers + 3 FC layers |
| Xception | Depthwise separable convs + linear stack of 36 conv layers |

---

## 📊 Results Comparison
### Using K-Means Clustered Data
| Model | Accuracy | Macro Precision | Macro Recall | Macro F1-Score |
|-------|----------|------------------|----------------|-----------------|
| AlexNet | 0.72 | 0.71 | 0.72 | 0.70 |
| DenseNet121 | 0.75 | 0.73 | 0.74 | 0.74 |
| InceptionV3 | 0.74 | 0.74 | 0.72 | 0.72 |
| MobileNetV2 | 0.77 | 0.75 | 0.76 | 0.75 |
| ResNet50 | 0.37 | 0.20 | 0.32 | 0.23 |
| VGG16 | 0.66 | 0.65 | 0.63 | 0.64 |
| VGG19 | 0.68 | 0.66 | 0.65 | 0.65 |
| Xception | 0.72 | 0.70 | 0.70 | 0.70 |

### Using Agglomerative Clustered Data
| Model | Accuracy | Macro Precision | Macro Recall | Macro F1-Score |
|-------|----------|------------------|----------------|-----------------|
| AlexNet | 0.84 | 0.82 | 0.86 | 0.83 |
| DenseNet121 | 0.83 | 0.81 | 0.83 | 0.82 |
| MobileNetV2 | 0.82 | 0.82 | 0.83 | 0.83 |
| Xception | 0.81 | 0.80 | 0.81 | 0.80 |
| InceptionV3 | 0.74 | 0.73 | 0.73 | 0.73 |
| VGG16 | 0.70 | 0.56 | 0.59 | 0.57 |
| VGG19 | 0.66 | 0.53 | 0.55 | 0.53 |
| ResNet50 | 0.42 | 0.34 | 0.34 | 0.34 |

---

## 🏆 Best Model
**AlexNet with Agglomerative Clustering** achieved the highest balance of performance:
- **Accuracy**: 0.84
- **F1 Score**: 0.83

---

## 🕵️‍♂️🔧👨🏻‍💻Testing on New Data Results

You can refer to the images from the Testing Folder

### Tested on K Means Clustering Models
| Model         | Testing Files/RottenMango_1.jpg | Testing Files/RottenMango_2.jpg | Testing Files/RottenMango_3.jpg |
|---------------|---------------------------------|---------------------------------|---------------------------------|
| **AlexNet** | Spoiled | Spoiled | Spoiled |
| **VGG16** | Spoiled | Spoiled | Spoiled |
| **VGG19** | Spoiled | Spoiled | Slate |
| **MobileNetV2** | Spoiled | Slate | Spoiled |
| **ResNet50** | Slate | Slate | Slate |
| **DenseNet121** | Spoiled | Spoiled | Spoiled |
| **InceptionV3** | Spoiled | Slate | Slate |
| **Xception** | Spoiled | Slate | Spoiled |

---

### Tested on Agglomerative Clustering Models
| Model         | Testing Files/RottenMango_1.jpg | Testing Files/RottenMango_2.jpg | Testing Files/RottenMango_3.jpg |
|---------------|---------------------------------|---------------------------------|---------------------------------|
| **AlexNet** | Slate | Slate | Rotten |
| **VGG16** | Rotten | Rotten | Rotten |
| **VGG19** | Rotten | Slate | Slate |
| **MobileNetV2** | Rotten | Slate | Slate |
| **ResNet50** | Rotten | Rotten | Rotten |
| **DenseNet121** | Rotten | Rotten | Rotten |
| **InceptionV3** | Rotten | Rotten | Rotten |
| **Xception** | Spoiled | Slate | Rotten |

---

## 📌 Future Scope
* Real-time quality detection using live camera feed integration
* Expansion to multi-class fruit classification for broader applicability
* Deployment on mobile devices using TensorFlow Lite or ONNX for real-time inference applications

