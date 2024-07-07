# SPIDER: Lumbar Spine Segmentation in MR Images

## Project Overview

This project, part of the Deep Learning Course CIT-654, focuses on developing a robust, automatic segmentation algorithm for lumbar spine MRI images. The segmentation covers key anatomical structures such as vertebrae, intervertebral discs (IVDs), and the spinal canal. The project utilizes a dataset of 447 T1- and T2-weighted sagittal MR series from 218 patients and leverages the MONAI framework for model implementation.

## Abstract

This project aims to advance the development of automatic image analysis methods for lumbar spine MRI. The continuous segmentation challenge encourages collaboration to improve lumbar spine MR interpretation through machine learning and help alleviate the global burden of low back pain.

## Objectives

1. **Dataset Presentation**: Introduce an extensive multi-center lumbar spine MRI dataset with reference segmentations for vertebrae, IVDs, and the spinal canal.
2. **Segmentation Challenge**: Establish a continuous lumbar spine MRI segmentation challenge for three anatomical structures in lumbar spine MRI.
3. **Performance Metrics**: Offer reference performance metrics for MONAI 3D, used to automatically segment all three spinal structures.

## Methodology

### Data Collection

- 257 lumbar spine studies collected, with each study consisting of up to three MRI series.
- Data sourced from four different hospitals in the Netherlands.

### Data Preprocessing

- Resampling and standardizing images to a unified size of (32, 128, 128).
- Unifying spacing and orientation.
- Saving new resampled files for model training.

### Network Architecture

- **Model Used**: UNETR (U-Net with Transformers) implemented using the MONAI framework.
- **Components**:
  - 3D Input Volume
  - Patching and Linear Projection
  - Transformer Encoder
  - Skip Connections
  - Decoder
  - Output Layer

### Training

- **Optimizer**: AdamW with a learning rate of 1e-4 and weight decay of 1e-5.
- **Loss Function**: Dice Cross Entropy Loss (DiceCELoss).
- **Training Loop**: Up to 21,000 iterations with evaluations every 1,000 iterations.
- **Best Model**: Determined by the highest validation Dice metric.

### Evaluation & Results

- **Metric Used**: Dice Metric to measure segmentation accuracy.
- **Results**:
  - Lowest loss: 0.15683
  - Best metric: 0.7154

## Conclusion

The developed spine medical segmentation model achieved an average Dice Score of 0.72, demonstrating its potential to assist healthcare professionals in saving time, reducing effort, and minimizing human error. The MONAI framework facilitated a smoother development process and improved performance.

## How to Use

### Requirements

- Python 3.x
- MONAI
- SimpleITK
- TQDM

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/AbdlhMhmd/spider-lumbar-segmentation.git
   ```
2. Navigate to the project directory:
   ```bash
   cd spider-lumbar-segmentation
   ```
3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Project

1. **Data Preparation**: Follow the preprocessing steps described in the report.
2. **Training the Model**:
   ```bash
   python train.py
   ```
3. **Evaluating the Model**:
   ```bash
   python evaluate.py
   ```

## Project Structure

- `code/`: Contains the Python scripts for data display, inspection, resampling, JSON file creation, MONAI model, and debugging codes.
- `presentation/`: Includes the presentation discussed with the professor.
- `report/`: Contains the detailed report documenting the steps and other related work.
