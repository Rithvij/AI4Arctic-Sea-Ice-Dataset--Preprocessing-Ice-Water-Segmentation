# AI4Arctic Sea Ice Challenge Ready-to-Train Dataset

The **AI4Arctic Sea Ice Challenge Ready-to-Train Dataset (v2)** is designed to help participants build machine learning models to detect and classify sea ice in **Synthetic Aperture Radar (SAR)** imagery, specifically from **Sentinel-1**. The dataset provides processed SAR images and corresponding sea ice masks (labels) that are used for training machine learning models in the context of the **AI4Arctic Sea Ice Challenge**.

## Table of Contents
- [Overview](#overview)
- [Dataset Description](#dataset-description)
  - [Input Data](#input-data)
  - [Target Labels](#target-labels)
- [Preprocessing](#preprocessing)
  - [Resizing](#resizing)
  - [Sea Ice Mask Modification](#sea-ice-mask-modification)
- [Training Process](#training-process)
- [Using the Dataset](#using-the-dataset)
- [Command to Extract the Dataset](#command-to-extract-the-dataset)
- [Acknowledgements](#acknowledgements)
- [Conclusion](#conclusion)

## Overview
The **AI4Arctic Sea Ice Challenge** aims to leverage machine learning to improve sea ice detection using **SAR imagery**. This dataset is a preprocessed version of the raw data, ready for training machine learning models. The dataset contains **SAR images** (from Sentinel-1) and their corresponding **sea ice masks (SOD)**, which serve as the ground truth for model training.

## Dataset Description

### Input Data
The input data consists of **SAR images** captured by **Sentinel-1** in **HH** (horizontal transmit, horizontal receive) and **HV** (horizontal transmit, vertical receive) polarizations. These polarization channels provide different views of the Earth's surface and are essential for accurately detecting sea ice.

- **HH and HV Polarization Channels**: These SAR data channels serve as features for model training, providing detailed information about the surface texture and properties of sea ice.
- **Downsampled Data**: The SAR images are resized to **1024x1024** pixels to make them more manageable for machine learning models.

### Target Labels
The **SOD** (Sea Ice Mask) is the ground truth label used for training. It indicates the areas in the image that correspond to sea ice.

- **SOD** (Sea Ice Mask): 
  - Values greater than 0 and less than 255 are classified as sea ice (`1`).
  - Values of `255` are considered invalid or missing data (`NaN`).
  
The **SOD** labels are used to train models to predict sea ice in the SAR images.

## Preprocessing

### Resizing
The SAR images (HH and HV polarizations) are resized to a standard resolution of **1024x1024** pixels to ensure consistency across the dataset. This resizing is performed using the `resize` function from the `skimage.transform` library.

### Sea Ice Mask Modification
The **SOD** masks are processed and cleaned to meet specific criteria:
- **Sea Ice Mask (`SOD`)**:
  - Pixels with values greater than 0 and less than 255 are set to `1`, representing sea ice.
  - Pixels with the value `255` are replaced with `NaN`, indicating missing or invalid data.

The modified masks are then used as labels for model training.

## Training Process
After preprocessing, the dataset is ready for training machine learning models like **U-Net** or **CNNs**. These models are trained to classify **sea ice** in SAR images using the following steps:
- **Input**: The SAR data from the HH and HV polarization channels.
- **Label**: The corresponding sea ice mask (SOD), which indicates where sea ice is located in the image.

During training, models are evaluated based on how well they predict the sea ice locations in unseen images.

## Using the Dataset
This dataset is designed for use in machine learning tasks, specifically for the detection of sea ice in SAR imagery. It is especially useful for training models like **U-Net** or **CNNs** that require labeled data for supervised learning.

To use this dataset:
1. Download the dataset from the **Earth Observation Training Data Lab (EOTDL)** using the command below.
2. Load the dataset into your machine learning pipeline.
3. Preprocess the dataset (if needed) according to the specifications.
4. Train a model using the processed input data and labels.

## Command to Extract the Dataset
To retrieve the **AI4Arctic Sea Ice Challenge Ready-to-Train Dataset (v2)**, use the following command from the **EOTDL** platform:
```bash
eotdl datasets get ai4arctic-sea-ice-challenge-ready-to-train -v 2
```

## Acknowledgements

- **AI4Arctic Sea Ice Challenge**: Dataset provided by the AI4Arctic Sea Ice Challenge.
- **Earth Observation Training Data Lab (EOTDL)**: For providing the tools to access and download the dataset.

## Conclusion

This repository provides a well-defined preprocessing pipeline to convert raw SAR and ice map data into a usable format for machine learning models. By following the steps outlined in this workflow, you can ensure that the data is properly prepared and augmented for training your sea ice detection models.

