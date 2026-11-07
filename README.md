# Computer Vision & Medical Image Analysis

Lecture notes, code, and real-life solutions for the **Computer Vision / Medical Image Analysis**, from the Health Informatics Research.

The journey covers the full pipeline of medical image analysis: from image acquisition, enhancement, and feature extraction to deep learning models for classification, detection, and segmentation, and on to transformers and generative models.

---

## Table of Contents

- [Course Roadmap](#course-roadmap)
- [Lecture Summaries](#lecture-summaries)
- [Home Tasks](#home-tasks)
- [Suggested Repository Structure](#suggested-repository-structure)
- [Getting Started](#getting-started)
- [Datasets](#datasets)

---

## Course Roadmap

| Lecture | Topic | Key Concepts |
|:-------:|-------|--------------|
| 1 | Computer Vision & Medical Imaging Overview | Imaging modalities, research tasks, challenges |
| 2 | Image Enhancement, Morphology & Augmentation | Gamma, CLAHE, filters, Fourier, erosion/dilation, geometric & photometric augmentation |
| 3 | Feature Extraction & Description | Handcrafted vs. deep features, GLCM, HOG, LBP, edges, corners |
| 5 | Deep Learning Models (CNNs) | CNN components, transfer learning, VGG-16, ResNet-50 |
| 6 | Optimizing Models for Medical Applications | Data imbalance, hyperparameter tuning |
| 8–9 | Image Segmentation | Thresholding, edge-based, region-based, clustering, contours |
| 12 | Generative AI | LLMs, GANs and their variants |
| 13 | U-Net Segmentation | Encoder–decoder architecture, skip connections |
| 14 | Semi-, Self-, and Unsupervised Learning | SimCLR, FixMatch, autoencoders, anomaly detection |
| Extra | Image Recognition & Object Detection | Bounding boxes, YOLO vs. R-CNN |
| Extra | Vision Transformers (ViT) | Patch embedding, self-attention, ViT variants |

---

## Lecture Summaries

### Lecture 1: Computer Vision

- **What it is:** a field of computer science focused on analyzing and processing images and video intelligently, enabling machines to understand images at the pixel level.
- **Research tasks in healthcare:** image processing (quality improvement), segmentation, object detection, and classification.
- **Medical imaging modalities covered:**
  - X-ray (chest radiography)
  - Fundus photography
  - Otoscopy
  - Ultrasound
  - MRI
  - Microscopy
  - Computerized Tomography (CT)
  - Optical Coherence Tomography (OCT)
  - Dermoscopy
  - Mammography (MG)
  - Histopathology
  - Endoscopy
  - Electrocardiogram (ECG/EKG)
- **Challenges in medical image analysis:**
  - Lack of high-quality labeled data
  - Variability in image acquisition and processing
  - Interpretability and explainability (black-box models)
  - Ethical and privacy concerns
  - Computational cost
  - Class imbalance
  - Generalization to unseen data
  - Model complexity
  - Human bias in data and algorithms

### Lecture 2: Image Enhancement, Morphology & Augmentation

**Image enhancement** modifies pixel values to improve visual quality and diagnostic accuracy (better contrast, noise reduction, feature enhancement, detail preservation).

| Category | Methods |
|----------|---------|
| Color enhancement | Color balance, saturation adjustment, color transfer, **gamma correction** |
| Histogram-based | Adaptive histogram equalization, **CLAHE** |
| Spatial filtering | Smoothing (**averaging filter**), sharpening (**unsharp masking**) |
| Frequency domain | **Fourier transformation**, low-pass and high-pass filtering |

**Morphological operations:** erosion, dilation, opening (erosion → dilation), closing (dilation → erosion), morphological gradient, top-hat, and black-hat.

**Image augmentation** artificially expands training data to reduce overfitting and handle limited data, imbalance, and anatomical variability.

- **Geometric:** rotation, zooming, translation, shearing, flipping
- **Photometric:** brightness, contrast, gamma, color channel shift, hue/saturation
- **Region-based:** cropping, padding, random erasing, patch-wise transforms
- **Noise/distortion:** Gaussian, salt-and-pepper, speckle noise, elastic transformations
- **Blur/sharpen:** Gaussian blur, motion blur, sharpening
- **Generative:** GAN-based synthesis, style transfer

### Lecture 3: Feature Extraction & Description

- **Handcrafted features:** rely on domain expertise (shape, texture, color, spatial relationships).
  - Geometrical/structural: area, perimeter, solidity, aspect ratio, circularity, convex hull, bounding box
  - Textural: GLCM (contrast, correlation, energy, homogeneity, entropy, dissimilarity), LBP, HOG, Gabor filters, GLRLM
- **Deep features:** hierarchical features learned automatically from data.
- **Local features:** Sobel edge detection, Canny edge detection (Gaussian smoothing → gradient → non-maximum suppression → double thresholding → hysteresis), corner detection (Harris, Shi-Tomasi).
- **Case study:** graph neural network–based breast cancer diagnosis on ultrasound images (BUSI dataset) using optimized graph construction and clinically relevant features (circularity, solidity, ellipse ratio, brightness, GLCM entropy, correlation, dissimilarity, contrast, energy, Shannon entropy).

### Lecture 5: Deep Learning Models (CNNs)

- Deep learning uses neural networks with three or more layers and extracts features automatically.
- **CNN components:** convolution layers, pooling layers, fully connected layers, output layer.
- **Transfer learning:** reuse a pre-trained model as a starting point (VGG16, VGG19, ResNet50, ResNet101, InceptionV3, Xception, …).
- **VGG-16:** 16 layers, simple and uniform architecture.
- **ResNet-50:** 50 layers with residual connections to address vanishing gradients.

### Lecture 6: Optimizing Models for Medical Applications

- **Data types:** balanced vs. imbalanced (e.g., 90% healthy / 10% diseased).
- **Classification types:** binary (e.g., COVID-19 positive/negative) and multi-class (e.g., normal/benign/malignant).
- **Hyperparameters:**
  - Learning rate (e.g., 0.0001 for medical imaging fine-tuning)
  - Activation functions (ReLU, Softmax, Sigmoid, Tanh)
  - Optimizers (Adam, Nadam, AdamW, RMSProp)
  - Batch size (small, e.g., 16 or 32, for limited data)
  - Epochs (fewer for large datasets, more for small or imbalanced ones)

### Lectures 8–9: Image Segmentation

Segmentation divides an image into regions based on features and properties; in medicine it is used to locate tumors, measure tissue volumes, simulate surgery, and navigate during surgery.

- **Thresholding:** splits pixels by intensity relative to a threshold T (constant or dynamic), producing a binary image.
- **Edge-based:** identifies object boundaries from contrast, texture, color, and saturation changes.
- **Region-based:** grows or merges regions from seed points.
- **Also covered:** clustering-based segmentation (e.g., k-means) and contour detection/extraction.

### Lecture 12: Generative AI

- Generative AI creates new content (audio, code, images, text, video) automatically.
- From language models to **Large Language Models (LLMs)**: scale has grown sharply since 2018 (GPT-1 → GPT-4, BERT, T5, PaLM).
- **Generative Adversarial Networks (GANs)** (Ian Goodfellow, 2014): a **generator** produces synthetic data while a **discriminator** classifies real vs. fake, trained adversarially.
- **Applications:** image generation, super-resolution, text-to-image synthesis, data augmentation, video generation, drug discovery.
- **Variants:** Vanilla GAN, CGAN, DCGAN, LAPGAN, SRGAN, StyleGAN, CycleGAN.

### Lecture 13: U-Net Segmentation

- A CNN designed for biomedical image segmentation.
- **Contracting path (encoder):** captures context with convolutions and pooling.
- **Bottleneck:** bridge between encoder and decoder.
- **Expanding path (decoder):** recovers spatial detail via upsampling and concatenation with high-resolution encoder features (skip connections).
- **Pipeline:** input image → encoder → decoder → binary or multi-class mask.
- **Applications:** tumor segmentation (MRI/CT), organ segmentation for surgical planning, skin lesion detection.

### Lecture 14: Semi-Supervised, Self-Supervised & Unsupervised Learning

| Aspect | Self-Supervised | Semi-Supervised | Unsupervised |
|--------|-----------------|-----------------|--------------|
| Labeled data | Only for fine-tuning | Mixed during training | None |
| Approach | Pretrain on unlabeled data, then fine-tune | Labeled + unlabeled together | Find patterns and structure |
| Example models | SimCLR, MoCo, BYOL | FixMatch, Mean Teacher | K-Means, GANs, Autoencoders |
| Medical use case | Pretraining an encoder for disease classification | Diagnosis with limited labels | Grouping images by similarity, anomaly detection |

### Extra: Image Recognition & Object Detection

- **Bounding box detection:** locate and label objects with rectangular boxes (R-CNN, YOLO).
- **YOLO (You Only Look Once):** a single network predicts bounding boxes and class probabilities in one pass. Architecture: backbone → neck → head. Medical uses: tumor detection, organ segmentation.
- **YOLO vs. R-CNN:** YOLO is fast and suited to real-time use but weaker on very small objects; R-CNN is more accurate (good with small objects) but slow.

### Extra: Vision Transformers (ViT)

- **Transformers:** encoder–decoder architectures built on self-attention (Query, Key, Value) and feed-forward networks.
- **ViT pipeline:** split image into patches → linear patch embedding → positional encoding → transformer encoder → classification head.
- **Variants:** DeiT (data-efficient), Swin (shifted windows), CvT (convolutional), CrossViT (dual-branch, multi-scale), PiT (pooling-based).
- **Medical applications:** image classification, segmentation, and integration with Electronic Health Records (EHRs).
- **Challenges:** large data requirements, high compute cost, and ongoing work on CNN–ViT hybrid models.

---

## Home Tasks

- [ ] **Lecture 2:** Apply two image enhancement techniques to a medical image; explore more geometric augmentation techniques and apply them to medical images; explain the differences between the original and enhanced images.
- [ ] **Lecture 3 (a):** Extract GLCM features (dissimilarity, correlation, homogeneity, contrast, energy at a 45° angle only) from an image dataset, save them to a CSV, and show its head and tail.
- [ ] **Lecture 3 (b):** Extract HOG features from an image directory, save them to a CSV, and show its head and tail.
- [ ] **Lecture 5:** Build a neural network to classify skin lesions (benign vs. malignant) using the ISIC dermoscopic image dataset.
- [ ] **Lecture 6:** Run a MobileNetV2 transfer learning model on the given dataset, perform hyperparameter tuning, and summarize the results in a table (submit as PDF).

---

## Suggested Repository Structure

```
.
├── README.md
├── lecture-01-computer-vision/
├── lecture-02-enhancement-augmentation/
├── lecture-03-feature-extraction/
│   ├── glcm_features.py
│   └── hog_features.py
├── lecture-05-cnn-skin-lesion/
├── lecture-06-hyperparameter-tuning/
│   └── mobilenetv2_tuning.ipynb
├── lecture-08-09-segmentation/
├── lecture-12-generative-ai/
├── lecture-13-unet/
├── lecture-14-self-semi-unsupervised/
├── extras/
│   ├── yolo-object-detection/
│   └── vision-transformer/
├── data/            # not tracked, see Datasets
└── requirements.txt
```

Adjust the folders to match how you organize your own work.

---

## Getting Started

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

# (Optional) create a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# Install typical dependencies
pip install numpy pandas matplotlib opencv-python scikit-image scikit-learn tensorflow
```

Typical libraries used across the course: **NumPy, pandas, Matplotlib, OpenCV, scikit-image, scikit-learn, TensorFlow/Keras (or PyTorch)**. Most exercises are designed to run in Google Colab.

---

## Datasets

| Dataset | Used for |
|---------|----------|
| [ISIC](https://www.isic-archive.com/) (International Skin Imaging Collaboration) | Skin lesion classification (Lecture 5) |
| BUSI (Breast Ultrasound Images) | Breast cancer diagnosis case study (Lecture 3) |
| Course-provided dataset | MobileNetV2 hyperparameter tuning (Lecture 6) |

Datasets are not included in this repository. Download them from their original sources and place them in the `data/` folder.
