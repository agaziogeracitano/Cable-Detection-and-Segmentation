# Cable Detection and Segmentation

* **Authors:** Agazio Geracitano, Vittorio Iusi.
* **Context:** Computer Vision Course - University of Calabria (2025/2026)

## Project Overview
This project addresses the challenge of detecting thin cables in noisy environments with complex geometries and varying lighting conditions. The solution utilizes Deep Learning segmentation techniques to identify and reconstruct cable lines, achieving high precision even in low-contrast scenarios.


## Methodology & Architecture
The solution is built upon a robust segmentation framework with several optimization strategies:

* **Architecture:** **UNet++** for high-quality segmentation masks.
* **Backbone:** **EfficientNet-B4** (pre-trained on ImageNet) used as the encoder.
* **Training Workflow:**
 *   1.  **Initial Training:** Standard training phase.
  *  2.  **Refinement Phase:** Fine-tuning with lower learning rates and checkpoint collection.
   * 3.  **Weight Averaging:** Averaging parameters from multiple best checkpoints to stabilize the model and improve generalization.
* **Data Augmentation:** Extensive use of geometric transformations (Flip, Rotation, GridDistortion) and CLAHE for contrast enhancement.

## Key Features (Notebook)
The `Cable_Detection_Notebook.ipynb` includes:
* **Custom Dataset Class:** Handling COCO format annotations.
* **Loss Function:** A combination of **Tversky Loss** and **Focal Loss** to handle class imbalance (thin cables vs large background).
* **Inference Strategy:**
  * **Heavy TTA (Test Time Augmentation):** Averaging predictions across 4 variants (Original, Flip Horizontal, Flip Vertical, Flip H+V).
  * **Deep Fishing:** Post-processing with a confidence threshold of 0.65.


