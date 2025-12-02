# ASS-DSS

A Python-based medical image analysis pipeline for aortic disease detection and classification, implementing nnUNet for segmentation and custom models for slice-level classification.

## Features

- **Step 1**: Image preprocessing and aorta mask generation using TotalSegmentator
- **Step 2**: Multi-class aortic disease segmentation using nnUNet (AD, IMH, PAU)
- **Step 3**: Slice-level disease classification using trained prediction models
- **GUI Interface**: User-friendly graphical interface with real-time logging

## Prerequisites

- Python 3.x
- Required Python packages (install via requirements.txt if available)
- TotalSegmentator executable
- Trained model weights (see Model Setup section)

## Input & Output

- **Input**: Folder containing `.nii.gz` format CTA images of the aorta
- **Output**: User-selected empty folder for storing processing results

## Model Setup

This pipeline requires pre-trained model weights for both segmentation and classification tasks:

### Segmentation Models (nnUNet)
- **Model 1**: Acute Dissection (AD) segmentation
- **Model 2**: Intramural Hematoma (IMH) segmentation  
- **Model 3**: Penetrating Atherosclerotic Ulcer (PAU) segmentation

**Required Format**: 
- Train your nnUNet models separately
- Place the trained model weights in the following directories:
  - `E:\nnunet\RESULTS_FOLDER\Dataset001_aortic\` (for AD segmentation)
  - `E:\nnunet\RESULTS_FOLDER\Dataset002_aortic\` (for IMH segmentation)
  - `E:\nnunet\RESULTS_FOLDER\Dataset003_aortic\` (for PAU segmentation)

### Prediction Models (Classification)
- **Model 1**: AD classification network
- **Model 2**: IMH classification network
- **Model 3**: PAU classification network

**Required Format**:
- Train your classification models separately
- Save trained weights as `.pth` files
- Place in the main directory or update the default paths in the GUI

## Installation

1. Clone this repository
2. Install required dependencies
3. Set up TotalSegmentator
4. Place trained model weights in appropriate directories

## Usage

1. Run `python main_controller.py`
2. Configure paths in the GUI:
   - Input folder containing `.nii.gz` CTA images
   - TotalSegmentator executable
   - Model paths (nnUNet and prediction models)
   - Output folder (empty folder for results)
3. Execute individual steps or run the full pipeline

## Pipeline Steps

- **Step 1**: Preprocess raw images and generate aorta masks
- **Step 2**: Perform multi-class segmentation using nnUNet models
- **Step 3**: Classify slices using trained prediction models

## Notes

- All model weights must be trained separately before using this pipeline
- The pipeline assumes a specific directory structure for nnUNet models
- Adjust default paths in the code if your model locations differ
- Ensure sufficient disk space and memory for processing medical images

## Requirements

- Medical image datasets for training (CT angiography)
- GPU resources for nnUNet inference
- Python environment with medical imaging libraries
