<img width="234" height="167" alt="image" src="https://github.com/user-attachments/assets/dd123697-f9f5-4c7f-8cf6-eba83fe645c2" />

># 🫁 A Comparative Study of CNN, Vision Transformer, and Hybrid-ViT Architectures for Multiclassification in Pneumonia 

> A systematic comparative study of Convolutional Neural Networks, Vision Transformers, and a Hybrid-ViT architecture on balanced, separately-augmented chest X-ray data for multi-class pneumonia detection.

Introduction
------------

Pneumonia, a respiratory infection caused by either viral or bacterial pathogens.In humans, the lungs contain tiny sacs called alveoli, which fill with air during healthy breathing.When pneumonia occurs, thes aveoli become filled with pus and fluid, causing discomfory and difficulty in breathing and restricting oxygen intake.Statistically, pneumonia impacts approximately 1,400 children per 100,000,contributing to 14% of fatalities among children below five years of age in 2019, resulting in the deaths of 740,180 children. In 2017, pneumonia caused over 808,000 deaths among children under five, representing 15% of all fatalities in this age group.The reduction in these figures can be
attributed to improved detection techniques and the development of health technologies such as vaccines.
The primary diagnostic tool for pneumonia is chest X-rays,where areas of infection are identified by white patches in the pulmonary region.

CNN:-
The CNN model examines connections between neighboring pixels within a specific receptive field defined by the filter size. Despite its effectiveness in capturing local spatial hierarchies, it struggles with recognizing relationships between distant pixels, which hinders its ability to understand the broader context and more complex patterns within an image. 
To overcome this limitation, recent advancements have integrated attention mechanisms, allowing the model to dynamically weigh the importance of pixels, regardless of their distance from each other. This enhancement helps capture both local and global dependencies more effectively.

Vision Transformer (ViT):-
Unlike CNNs, which are restricted by the local receptive field of filters, the Vision Transformer (ViT) architecture abandons convolutions entirely in favor of Self-Attention mechanisms. It treats an image as a sequence of patches (visual tokens), allowing every pixel to interact with every other pixel across the entire image simultaneously.

Hybrid-ViT :-
The Hybrid-ViT architecture represents the current state-of-the-art for your pneumonia classification task. It combines the best of both worlds: using a CNN backbone (like ResNet or BiT) to extract low-level spatial features (textures and edges) and Transformer blocks to process those features with global attention.

## 📌 Overview

There are 4 classes of dataset that had taken.

| Class | Description |
|-------|-------------|
| `Normal` | Healthy chest X-ray |
| `Viral Pneumonia` | Pneumonia caused by viral infection |
| `Bacterial Pneumonia` | Pneumonia caused by bacterial infection |
| `COVID-19 Pneumonia` | Pneumonia associated with SARS-CoV-2 |

## Methodology

Data Collection
---------------

From Kaggle

The data was took from kaggle(https://www.kaggle.com/datasets/mohamedasak/chest-x-ray-6-classes-dataset)
After adding all the data it became as 
#Covid-2717
#Normal-2971
#Bacterial-2699
#Viral-2713
I want to make it balanced so i made all 2699 samples in each class .
The total it became 10784.

Data Augumentation

The made data Augumentation seperately for CNN and Vision Transformer architectures because CNN images should focuses on features,
1>For CNN
Added specific CNN parameters like Rotation (15 degrees),Width/Height Shift (10%),Zoom (15%), Brightness (0.8 to 1.2),Horizontal Flip, and standardized the size for CNN as 224,224,
2>For ViT
Added  Random Resized Crop (Crucial for ViT Patch learning), Horizontal Flip,Color Jitter (Brightness and Contrast),Gaussian Blur (To force ViT to look at global structures, not just noise),

Data Preprocessing
-------------------

Train Test Split
The dataset was then divided into training,testing,validation subsets with proportion of 80%,10%,10%


A key methodological contribution is the use of **class-balanced datasets with class-wise separate augmentation**, ensuring no data leakage between augmented splits and a fair comparison across architectures.

---
Model architectures
-------------------

CNN

1>AlexNet
Architecture:
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/167d1bf9-6c2c-498c-b919-16f5804808d4" />
(Source:-https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f7640161)
Results:-
<img width="908" height="702" alt="image" src="https://github.com/user-attachments/assets/0473e478-b177-4240-a61b-3f16b53f49d2" />
<img width="587" height="297" alt="image" src="https://github.com/user-attachments/assets/90782dfb-b9c4-47b9-9d57-5b7c065b9ccd" />

2>DenseNet121
Architecture:
<img width="1200" height="646" alt="image" src="https://github.com/user-attachments/assets/ead3d030-ebdf-4c04-af8f-53e9cea3aac9" />

(Source:-[https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f7640161)](https://medium.com/deepkapha-notes/implementing-densenet-121-in-pytorch-a-step-by-step-guide-c0c2625c2a60)
Results:-
<img width="893" height="698" alt="image" src="https://github.com/user-attachments/assets/39dc428c-fe2e-4ef0-989b-bf89fc8057d4" />
<img width="556" height="292" alt="image" src="https://github.com/user-attachments/assets/2e94d2eb-e905-4d4b-b16c-f05f5313c3aa" />
<img width="947" height="712" alt="image" src="https://github.com/user-attachments/assets/bd5cdd0c-db20-4644-9cf1-0ba7fef3a89d" />

3>EfficientNetB0
Architecture:
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/167d1bf9-6c2c-498c-b919-16f5804808d4" />
(Source:-https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f7640161)
Results:-
<img width="851" height="716" alt="image" src="https://github.com/user-attachments/assets/fc042a1c-3446-41a4-8f77-f1caf05de5a8" />
<img width="823" height="305" alt="image" src="https://github.com/user-attachments/assets/50d49aca-4e5c-4ec5-8f83-066a368ea2b8" />
<img width="925" height="705" alt="image" src="https://github.com/user-attachments/assets/a690e44c-c0bd-47b8-a25f-182f5918f099" />


4>InceptionV3
Architecture:
<img width="307" height="164" alt="image" src="https://github.com/user-attachments/assets/88f42130-f476-4697-85ab-722e0a82a771" />


(Source:[researchgate.net/figure/Architecture-of-EfficientNet-B0-with-MBConv-as-Basic-building-blocks_fig4_344410350](https://www.researchgate.net/figure/Architecture-of-Inception-v3_fig3_364173580))
Results:-
<img width="844" height="701" alt="image" src="https://github.com/user-attachments/assets/26fef1d7-7019-4df0-a694-ceb89496ba75" />
<img width="635" height="302" alt="image" src="https://github.com/user-attachments/assets/be6347f9-2e8b-4e20-a40e-a428c57a13f0" />

<img width="948" height="708" alt="image" src="https://github.com/user-attachments/assets/7d1527a6-1fff-4976-9296-7c306afe1f89" />

5>ResNet50
Architecture:
<img width="3744" height="1206" alt="image" src="https://github.com/user-attachments/assets/6ac77f86-519a-42af-8df2-04f4b37b446a" />

(Source:-[https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f7640161](https://towardsdatascience.com/the-annotated-resnet-50-a6c536034758/)
Results:-
<img width="882" height="703" alt="image" src="https://github.com/user-attachments/assets/6f3e1959-eb47-4582-ab9c-e458e31879a7" />
<img width="869" height="301" alt="image" src="https://github.com/user-attachments/assets/be4b5a73-1592-4776-9af4-0bbc2cf6e024" />

<img width="968" height="721" alt="image" src="https://github.com/user-attachments/assets/416f9523-8822-4e4e-a9ee-c401037a0c91" />


6>SqueezeNet
Architecture:
<img width="265" height="190" alt="image" src="https://github.com/user-attachments/assets/eb15a04e-2fd1-4a41-ab2a-ce5d7a62019a" />


(Source:-[https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f764016](https://www.researchgate.net/figure/SqueezeNet-Architecture-30_fig1_340359609)
Results:-
<img width="908" height="702" alt="image" src="https://github.com/user-attachments/assets/0473e478-b177-4240-a61b-3f16b53f49d2" />
<img width="587" height="297" alt="image" src="https://github.com/user-attachments/assets/90782dfb-b9c4-47b9-9d57-5b7c065b9ccd" />
<img width="943" height="718" alt="image" src="https://github.com/user-attachments/assets/dc0a57f3-32c7-481c-a4dd-0f1e7633f055" />

7>VGG19
Architecture:
<img width="1043" height="746" alt="image" src="https://github.com/user-attachments/assets/d038cc3e-33d8-49c1-ba1d-2aa9770d244e" />

(Source:-[https://medium.com/@abhishekjainindore24/deep-learning-architecture-2-alexnet-8018f7640161](https://www.geeksforgeeks.org/computer-vision/vgg-net-architecture-explained/)
Results:-
<img width="924" height="710" alt="image" src="https://github.com/user-attachments/assets/620121b0-07e7-403f-a28e-c0ef8c3c480b" />
<img width="884" height="290" alt="image" src="https://github.com/user-attachments/assets/b4600cc4-4e25-4008-8a1e-e63931b25c52" />

<img width="989" height="714" alt="image" src="https://github.com/user-attachments/assets/60681183-ad9d-4721-a6b3-ad20962b398f" />


ViT
-----

1>BEiT(BerT pre-training image transformer)
Architecture:
<img width="922" height="493" alt="image" src="https://github.com/user-attachments/assets/a05d55bc-d97f-4a32-86a6-22a9530f891a" />
(Source:https://sh-tsang.medium.com/review-beit-bert-pre-training-of-image-transformers-c14a7ef7e295)
Results:
<img width="816" height="289" alt="image" src="https://github.com/user-attachments/assets/9d749c54-9740-4e19-aae0-90c2ffa0e051" />
<img width="938" height="717" alt="image" src="https://github.com/user-attachments/assets/3c344bd2-5aad-4c2b-b0e6-4d2a0b0862ff" />
<img width="993" height="714" alt="image" src="https://github.com/user-attachments/assets/8449ce31-b38a-40f9-8454-0ca3662d6bfe" />


2>Swim Transformer
Architecture:
<img width="2108" height="611" alt="image" src="https://github.com/user-attachments/assets/d91443ed-77f8-4f58-9cef-5792c8bbf2b0" />
(Source:-https://mmpretrain.readthedocs.io/en/latest/papers/swin_transformer.html)

Results:-<img width="941" height="687" alt="image" src="https://github.com/user-attachments/assets/65ef5f5b-5459-40a5-9bea-43ff160b5ae6" />
<img width="904" height="304" alt="image" src="https://github.com/user-attachments/assets/cb08935c-5178-4564-b3a5-1ee991803d36" />

3>ViT-B/16

Architecture:
<img width="1400" height="713" alt="image" src="https://github.com/user-attachments/assets/0517bd31-9bc1-4762-a7bf-5e742a29d650" />
(Source:-https://sh-tsang.medium.com/review-vision-transformer-vit-406568603de0)

Results:-
<img width="902" height="704" alt="image" src="https://github.com/user-attachments/assets/a651ba18-37ce-4e06-b21d-278ed80faff1" />
<img width="648" height="307" alt="image" src="https://github.com/user-attachments/assets/7f601ccb-aa42-41ee-8ff7-e26220b2368f" />


Hybrid_ViT
-----------
1>BoTNet
Architecture:
<img width="441" height="318" alt="image" src="https://github.com/user-attachments/assets/0f681c8b-5fb5-4bf9-96e0-ebdf4e49acf5" />
(Source:-https://sh-tsang.medium.com/brief-review-botnet-bottleneck-transformers-for-visual-recognition-bc2d4878cab7)
Rdesults:-
<img width="892" height="699" alt="image" src="https://github.com/user-attachments/assets/cd29733e-128a-4b5a-9e5d-26d8392d58bb" />
<img width="790" height="296" alt="image" src="https://github.com/user-attachments/assets/7c446e86-c4d0-4e6c-a4f7-d6d66afe3660" />
<img width="1048" height="266" alt="image" src="https://github.com/user-attachments/assets/907357e2-8829-40eb-8b94-243da550a507" />
<img width="1021" height="269" alt="image" src="https://github.com/user-attachments/assets/172d9226-1b47-4579-b035-68a0129ad4b5" />


---

## 🗂️ Repository Structure

```
CNN_ViT_Hybrid_ViT_Research_Pneumonia_4_Classification/
│
├── Data_Collection/              # Raw dataset collection scripts & sources
├── Unique_Raw/                   # Deduplicated raw X-ray images
├── Raw/                          # Original raw images per class
│
├── Equal_sample/                 # Class-balanced subset (equal N per class)
│
├── Data_Augmentation/            # Augmentation scripts (applied per class separately)
│
├── CNN_Augmented_Data/           # Augmented data prepared for CNN training
├── Vit_Augmented_Data/           # Augmented data prepared for ViT training
│
├── Train_Test_Split_CNN_Data/    # Final train/test splits for CNN
├── Train_Test_Split_Vit_Data/    # Final train/test splits for ViT & Hybrid-ViT
│
├── CNN/                          # CNN model — architecture, training, evaluation
├── ViT/                          # Vision Transformer — architecture, training, evaluation
├── Hybrid_Vit/                   # Hybrid-ViT — CNN feature extractor + ViT encoder
│
├── Analysis.xlsx                 # Consolidated metrics comparison across all models
└── README.md
```

---

## 🔄 Data Pipeline

The data pipeline is designed to be reproducible and bias-free:

```
Raw X-rays
    ↓
Deduplication (Unique_Raw)
    ↓
Class Balancing — Equal samples per class (Equal_sample)
    ↓
Per-Class Augmentation (Data_Augmentation)
    ↓                          ↓
CNN_Augmented_Data      Vit_Augmented_Data
    ↓                          ↓
Train/Test Split        Train/Test Split
(CNN)                   (ViT / Hybrid-ViT)
    ↓                          ↓
CNN Training          ViT / Hybrid-ViT Training
```

> ⚠️ **Important:** Augmentation is performed **before** splitting, but applied **per class independently**, ensuring class distributions are preserved and no augmented sample from the test set contaminates training.


Analysis
----------

<img width="1067" height="596" alt="image" src="https://github.com/user-attachments/assets/317fc98d-cd1d-4706-b31e-84e33a48cc05" />



