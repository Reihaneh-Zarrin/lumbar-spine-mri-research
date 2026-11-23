# Lumbar Spine MRI Research: Dataset Assessment and Literature Analysis

## 1. Research Objective

The initial objective of this project was to identify a suitable spinal imaging dataset and assess whether it could support a meaningful research study involving automated analysis of spinal conditions. The work focused on understanding the available data, reviewing existing approaches to MRI-based spinal assessment, and identifying a feasible research direction.

## 2. Dataset Assessment

### 2.1 Main MRI Dataset

**Source:** [Mendeley Data – Dataset k57fr854j2, Version 2](https://data.mendeley.com/datasets/k57fr854j2/2)

The dataset contains anonymized clinical MRI studies from **515 patients with symptomatic back pain**. A patient may have one or more MRI studies, and each study contains multiple image slices.

The scans cover the lowest three vertebrae and the lowest three intervertebral discs (IVDs), with sagittal and axial views:

- **Axial view:** Usually includes slices from the last three IVDs, including the disc between the lowest vertebra and the sacrum. There are generally 4–5 slices per IVD, with approximately 12–15 axial slices per study; some studies contain up to 20.
- **Sagittal view:** Each scan includes at least the last seven vertebrae and the sacrum, including the first two sacral segments.

### 2.2 Image Characteristics and Technical Metadata

- **Total number of MRI slices:** 48,345.
- **Image resolution:** Most slices are 320 × 320 pixels; three studies contain slices with a resolution of 320 × 310 pixels.
- **Pixel precision:** 12 bits per pixel.
- **Axial slice thickness:** 4 mm.
- **Axial centre-to-centre slice distance:** 4.4 mm.
- **Axial pixel spacing:** 0.6875 mm horizontally and vertically.
- **File format:** DICOM (Digital Imaging and Communications in Medicine).
- **Patient position:** Most studies were acquired in Head-First-Supine position; the remainder were acquired in Feet-First-Supine position.
- **Study duration:** Approximately 15–45 minutes.

The DICOM metadata can contain information such as modality, scanner manufacturer and model, body part examined, patient sex, patient age, patient size and weight, acquisition parameters, image orientation, and patient position.

An example metadata record in the original dataset report contains:
- Modality: MR
- Manufacturer: SIEMENS
- Body part examined: LSPINE
- Patient sex: M
- Patient age: 053Y
- Patient identity removed: YES
- Magnetic field strength: 1.5 T
- Patient position: HFS

**Important:** These values are from an example metadata record. They should not be interpreted as the sex or age distribution of the full dataset.

### 2.3 Availability of Labels

A separate dataset provides raw label images and ground-truth label images for **axial-view slices** of lumbar spine MRI. The annotations were created by five labellers under the supervision of an expert radiologist, using T1-weighted axial MRI slices from the last three IVDs.

Four regions of interest (ROIs) are annotated:

1. Intervertebral Disc (IVD)
2. Posterior Element (PE)
3. Thecal Sac (TS)
4. Area between Anterior and Posterior (AAP) vertebral elements

The labels were developed for training SegNet to detect lumbar spinal stenosis. The availability of these annotations is useful, but their scope is specific: they concern selected axial-view slices and four anatomical regions, rather than providing comprehensive diagnostic labels for every image and every spinal condition.

## 3. Review of Existing Research

The reviewed studies were organized into two broad groups: **detection and classification**, and **grading or severity assessment**. The studies use different datasets, imaging views, target conditions, model architectures, and evaluation metrics. Their reported results therefore cannot always be compared directly.

### 3.1 Detection and Classification

#### 1. Automatic Detection, Classification, and Grading of Lumbar Intervertebral Disc Degeneration Using an Artificial Neural Network Model

- **Task:** Detection, classification, and grading of intervertebral disc degeneration (IDD).
- **Model:** Deep CNN / YOLOv5.
- **Reported result:** Accuracy above 95%.

#### 2. Lumbar Spine Discs Classification Based on Deep Convolutional Neural Networks Using Axial View MRI

- **Task:** Classification of lumbar disc condition.
- **Model:** CNN based on VGG16.
- **Reported result:** 94% accuracy.

#### 3. Deep Learning Model for Automated Detection and Classification of Central Canal, Lateral Recess, and Neural Foraminal Stenosis at Lumbar Spine MRI

- **Task:** Detection and classification of lumbar spinal stenosis in different anatomical regions.
- **Model:** CNN.
- **Reported result:** κ values of 0.95–0.96 for different regions of interest.

#### 4. Deep Learning-Based Detection and Classification of Lumbar Disc Herniation on Magnetic Resonance Images

- **Task:** Detection and classification of lumbar disc herniation.
- **Model:** Faster R-CNN and ResNeXt101.
- **Internal test results:** Accuracy 87.7%; AUC 0.965; ICC 0.87; precision 98.4%; sensitivity 99.4%.
- **External test results:** Accuracy 74.2%; AUC 0.916; ICC 0.79; precision 96.3%; sensitivity 97.8%.

#### 5. Automatic Classification of the Vertebral Endplate Lesions in Magnetic Resonance Imaging by Deep Learning Model

- **Task:** Automatic classification of vertebral endplate lesions in MRI scans.
- **Model:** CNN-based model (ResNet18), fine-tuned on T2-weighted MRI data.
- **Reported result:** 88% accuracy.

#### 6. Faster R-CNN-Based Detection of Cervical Spinal Cord Injury and Disc Degeneration

- **Task:** Detection and classification of lesions in MRI images associated with cervical spinal cord conditions.
- **Model:** Faster R-CNN with ResNet-50 and VGG-16 feature-extraction backbones.
- **Reported result:** mAP of 88.6 with ResNet-50 and 72.3 with VGG-16.

#### 7. Automatically Diagnosing Disk Bulge and Disk Herniation With Lumbar Magnetic Resonance Images by Using Deep Convolutional Neural Networks: Method Development Study

- **Task:** Identification of IVD positions and classification of normal discs, disc bulges, and disc herniations.
- **Model:** Faster R-CNN and ResNet-10.
- **Reported accuracy by disc level:**
  - L1–L2: 92.7%
  - L2–L3: 84.4%
  - L3–L4: 92.1%
  - L4–L5: 90.4%
  - L5–S1: 84.2%

#### 8. Automated Detection and Measurement of Dural Sac Cross-Sectional Area in Lumbar Spine MRI Using Deep Learning

- **Task:** Automated detection and measurement of dural sac cross-sectional area (DSCA), a measurement relevant to the assessment of spinal conditions including stenosis.
- **Models:** U-Net, Attention U-Net, and MultiResUNet.
- **Reported results:**
  - U-Net: 0.9990 on the initial dataset; 0.9987 on external validation.
  - Attention U-Net: 0.9992 on the initial dataset; 0.9989 on external validation.
  - MultiResUNet: 0.9996 on the initial dataset; 0.9995 on external validation.

#### 9. Spinal Disease Diagnosis Assistant Based on MRI Images Using Deep Transfer Learning Methods

- **Task:** Classification of normal spines, IVD bulges, and spondylolisthesis from MRI images.
- **Models:** YOLOv3, YOLOv5, and PP-YOLOv2.
- **Reported results:** Overall accuracy / mAP of 90.08%; accuracy of 93.84% for normal cases, 91.74% for IVD bulges, and 84.67% for spondylolisthesis. The reported mAP was higher than YOLOv3 and YOLOv5 by 27.5% and 3.9%, respectively.

#### 10. A Neural Network Model for Detection and Classification of Lumbar Spinal Stenosis on MRI

- **Task:** Classification of central canal, lateral recess, and foraminal stenosis, with severity categories of absent, mild, moderate, or severe.
- **Model:** CNN.
- **Reported results:**
  - Central canal stenosis: sensitivity 0.971, specificity 0.864, AUROC 0.963.
  - Lateral recess stenosis: sensitivity 0.853, specificity 0.787, AUROC 0.907.
  - Foraminal stenosis: sensitivity 0.942, specificity 0.844, AUROC 0.950.

#### 11. Detection of Degenerative Changes on MR Images of the Lumbar Spine with a Convolutional Neural Network: A Feasibility Study

- **Task:** Detection and labeling of vertebrae and disc segments, as well as detection of disc herniation, disc bulging, spinal canal stenosis, nerve root compression, and spondylolisthesis.
- **Model:** CNN with a U-Net-based architecture.
- **Reported results:**
  - Intervertebral disc detection and labeling: 100% accuracy.
  - Disc herniation: 87% accuracy (95% CI: 0.84–0.89).
  - Extrusions: 86% accuracy (95% CI: 0.84–0.89).
  - Bulging discs: 76% accuracy (95% CI: 0.73–0.78).
  - Spinal canal stenosis: 98% accuracy (95% CI: 0.97–0.99).
  - Nerve root compression: 91% accuracy (95% CI: 0.89–0.92).
  - Spondylolisthesis: 87.61% accuracy (95% CI: 85.26–89.21).

### 3.2 Grading and Severity Assessment

#### 1. A Neural Network Model for Detection and Classification of Lumbar Spinal Stenosis on MRI

- **Task:** Classification of central, lateral recess, and foraminal stenosis, including severity levels (absent, mild, moderate, or severe).
- **Model:** Three-stage CNN.
- **Reported results:**
  - Central canal stenosis: sensitivity 0.971, specificity 0.864, AUROC 0.963.
  - Lateral recess stenosis: sensitivity 0.853, specificity 0.787, AUROC 0.907.
  - Foraminal stenosis: sensitivity 0.942, specificity 0.844, AUROC 0.950.

#### 2. Deep Learning Model for Grading and Localization of Lumbar Disc Herniation on Magnetic Resonance Imaging

- **Task:** Grading and localization of lumbar disc herniation (LDH).
- **Model:** Deep learning model for grading and localization.
- **Reported results:**
  - Internal testing: grading IoU 0.84; localization IoU 0.82.
  - External testing: grading IoU 0.72; localization IoU 0.71.
  - Grading sensitivity: 87%; specificity: 95.5%.

#### 3. Artificial Intelligence Classification for Detecting and Grading Lumbar Intervertebral Disc Degeneration

- **Task:** Grading lumbar intervertebral disc degeneration using the Pfirrmann grading system.
- **Model:** CNN with a YOLO architecture.
- **Reported results:**
  - Overall ROC-AUC: 97% (training), 92% (testing), and 95% (validation).
  - Grade-specific metrics were also reported: Grade I accuracy of 97%, 95%, and 92% across training, testing, and external validation; Grade II sensitivity of 100% in training and testing and 98% in validation; Grade III specificity of 95.4% in training and 94% in testing/validation; Grade IV F1 score of 97.77% in training and 95% in testing/validation.
- **Grading system:** The Pfirrmann system classifies disc degeneration from Grade I (healthy) to Grade V (severe), based on MRI characteristics such as disc height, signal intensity, and structure.

#### 4. A Deep Learning Model for the Accurate and Reliable Classification of Disc Degeneration Based on MRI Data

- **Task:** Classification of intervertebral disc degeneration using the Pfirrmann grading scheme.
- **Model:** Deep CNN.
- **Reported results:** Cohen’s κ 0.92; sensitivity 90.2%; precision 92.5%; mean absolute error 0.08 Pfirrmann grade; correlation r = 0.96.

#### 5. Automated Detection and Measurement of Dural Sac Cross-Sectional Area in Lumbar Spine MRI Using Deep Learning

- **Task:** Measurement of dural sac cross-sectional area (DSCA), which can contribute to the assessment of spinal stenosis severity.
- **Models:** U-Net, Attention U-Net, and MultiResUNet.
- **Reported results:**
  - U-Net: 0.9990 on the initial dataset; 0.9987 on external validation.
  - Attention U-Net: 0.9992 on the initial dataset; 0.9989 on external validation.
  - MultiResUNet: 0.9996 on the initial dataset; 0.9995 on external validation.

#### 6. Automatic Grading of Disc Herniation, Central Canal Stenosis and Nerve Roots Compression in Lumbar Magnetic Resonance Image Diagnosis

- **Task:** Grading lumbar disc herniation (LDH), lumbar central canal stenosis (LCCS), and lumbar nerve root compression (LNRC) using axial MRI scans.
- **Model:** Multi-task classification model based on ResNet-50.
- **Reported results:**
  - LDH grading accuracy: 84.17% (internal), 74.16% (external).
  - LCCS grading accuracy: 86.99% (internal), 79.65% (external).
  - LNRC grading accuracy: 81.21% (internal), 74.16% (external).
  - Inter-rater agreement: Gwet’s κ 0.67–0.85.

#### 7. Automatic Detection, Classification, and Grading of Lumbar Intervertebral Disc Degeneration Using an Artificial Neural Network Model

- **Task:** Grading intervertebral disc degeneration (IDD) using the Pfirrmann grading system.
- **Model:** Deep CNN.
- **Reported result:** Detection and grading accuracy above 95%.
- **Reported class distribution:** Grade I: 220 discs; Grade II: 530; Grade III: 170; Grade IV: 160; Grade V: 20.

#### 8. Lumbar Spine MRI Annotation with Intervertebral Disc Height and Pfirrmann Grade Predictions

- **Task:** Prediction of Pfirrmann grade and estimation of intervertebral disc height.
- **Model:** ResNet-50 combined with an ensemble of decision trees.
- **Reported result:** Grading accuracy of 88%.

#### 9. Spinal Stenosis Grading in Magnetic Resonance Imaging Using Deep Convolutional Neural Networks

- **Task:** Grading spinal stenosis based on the degree of spinal canal narrowing.
- **Models:** Faster R-CNN for detection and VGG for classification.
- **Reported results:** Expert agreement of 77.5% accuracy and 75% F1 score; model agreement of 83% accuracy with Expert 1 and 77.9% with Expert 2.

#### 10. Learning-Based Fully Automated Prediction of Lumbar Disc Degeneration Progression

- **Task:** Prediction of lumbar disc degeneration progression over time using Pfirrmann grading, Schneiderman score, and disc bulging.
- **Model:** VGG-M combined with MRI-SegFlow.
- **Reported results:**
  - Schneiderman score: 90.2% ± 0.9% accuracy.
  - Disc bulging: 90.4% ± 1.1% accuracy.
  - Pfirrmann grading: 89.9% ± 2.1% accuracy.

## 4. Comparative Observations

The reviewed studies demonstrate that deep learning methods have been applied to a wide range of lumbar spine MRI tasks, including disc degeneration grading, disc herniation detection, spinal stenosis classification, anatomical localization, and measurement of relevant structures.

Several studies report strong internal evaluation results. However, performance may decrease on external datasets. For example, the lumbar disc herniation study reported a reduction in accuracy from 87.7% on its internal test set to 74.2% on its external test set. Other studies also report different metrics and target different conditions, making direct ranking of their performance unreliable.

The review also showed that apparently similar tasks may rely on different imaging views, annotation protocols, grading systems, and definitions of the target condition. Consequently, a model or result from one study could not automatically be transferred to another dataset or research setting.

## 5. Project Outcome and Feasibility Assessment

The project began with the aim of identifying a suitable spinal MRI dataset and finding a research direction in which the available data could support a meaningful analysis. The dataset assessment and review of existing studies helped clarify both the available data and the extent of work already carried out in this area.

Although the literature showed promising results, identifying a feasible contribution required more than finding a model with a lower reported score. The studies differed in their datasets, labels, imaging protocols, and evaluation methods, while the available data and annotations did not necessarily match the requirements of the potential research directions.

After assessing the available dataset and examining the existing approaches, we concluded that, within the data, resources, and technical scope available to our team at the time, we could not identify a sufficiently well-defined and achievable direction that would allow us to make a meaningful improvement over the existing work. In particular, the limitations of the available data made it difficult to proceed with a robust experimental study. We therefore decided not to continue with model development.

This outcome was a feasibility assessment rather than evidence that the research area has no remaining opportunities for improvement. The work provided a clearer understanding of the available spinal MRI data, existing methods, annotation requirements, and practical constraints that would need to be addressed in a future study.

## 6. Scope and Limitations of This Report

This document organizes the dataset investigation and literature notes collected during the project. The reported model results are reproduced from the original notes and should be checked against the corresponding papers before being used in a formal publication or presented as a systematic comparison. The studies use different datasets and evaluation protocols, so the reported metrics should not be treated as directly comparable.

The original notes did not include complete bibliographic details or links for every paper. Full references should be added before public release of this report.
