# MTL-NucleusSeg
Revolutionizing multi-organ nucleus segmentation in histopathological images with a cutting-edge multi-task learning framework to effectively handle challenges like dense nuclei packing, overlapping structures, and staining variability.

This repository contains the implementation of a novel multi-organ nucleus segmentation framework

## Overview of Methodology
![compressed_3model_arch](https://github.com/user-attachments/assets/c6fd2779-ec4f-4d01-ac09-10972ff0bc24)

## Key Features
### 1. Pre-Processing and  Style Transformation to Standardize Variability 

This stage ensures consistent quality across histopathological datasets by addressing staining intensity variations and preparing reliable training data.

- [x] **Reference Selection:** Criteria to identify representative reference images for style transfer.

- [x] **Style Transfer:** Harmonization of visual characteristics across datasets.

- [x] **Label Crafting:** Preparation of high-quality training data to enhance model reliability.
![pre_processing](https://github.com/user-attachments/assets/c2dcd897-0423-4651-ab4a-2aae850b66a7)

### 2. Proposed Model Architecture
The framework employs a multi-task learning model with an encoder-decoder structure, integrating advanced techniques for effective segmentation Multi-Dilated Residual Block with Bottleneck Transformer:
Multi-dilated convolutions capture features at varying scales, improving segmentation in dense and overlapping regions. Bottleneck Transformer ensures long-range dependency modeling. Attention Gate Mechanisms: Focuses on relevant regions of interest, enhancing segmentation accuracy.

#### Dual Output Heads:
- [x] **Distance Map $\( D \in \mathbb{R}^{H \times W} \)$:** Encodes spatial relationships to separate densely packed nuclei.

- [x] **Semantic Segmentation Map $\( S \in \mathbb{R}^{H \times W} \)$:** Classifies pixels as nucleus or background.
      
![model](https://github.com/user-attachments/assets/e60b3cbe-ba47-49fa-87b0-3a89c18b7fc2)

#### Post-processing
To achieve instance segmentation using the outputs from our proposed multi-task model.

![post_processing](https://github.com/user-attachments/assets/c4733192-3ca6-47e4-ac77-75c7739240c3)


## Results
Our proposed model was trained and evaluated on two multi-organ segmentation benchmark datasets: NuInsSeg and MoNuSeg. Below figure present representative segmentation results from the NuInsSeg and MoNuSeg datasets. The proposed framework achieves state-of-the-art performance on   NuInsSeg dataset, and comparative result on the MoNuSeg dataset:

![compressed NuInsSEG and MonuSeg result](https://github.com/user-attachments/assets/efe684be-948c-4133-b62c-8d36d5227089)


## Comparation




## Repository Structure

- **preprocessing/**  
  Contains scripts for reference selection, style transfer, and data augmentation.

- **training.ipynb**  
  Jupyter Notebook for training the multi-task learning model.

- **test.ipynb**  
  Jupyter Notebook for testing the multi-task learning model.

- **Saved_model/**  
  Pretrained models for both the NuInsSeg and MoNuSeg datasets.

- **evaluation/**  
  Scripts for calculating evaluation metrics such as Dice, IoU, AJI, and PQ.

- **datasets/**  
  Scripts for dataset preparation and implementing 5-fold cross-validation.

---
## Installation

Clone the repository:  
```bash
git clone https://github.com/eyob12/MTL-NucleusSeg.git 
cd MTL-NucleusSeg 

```
## Install Dependencies
  
Install the required Python dependencies:\  
```bash
 pip install -r requirements.txt 


```
# Usage
## Data Preprocessing
Use the provided script to apply style transfer and augmentations:
```bash
python preprocess.py --input_dir <path-to-dataset> --output_dir <path-to-output>

```
## Train the Model
Start training with:
```bash
python train.py --config config.yaml
```
## Evaluate the Model
Evaluate on test datasets with:
```bash
python evaluate.py --weights <path-to-weights>
