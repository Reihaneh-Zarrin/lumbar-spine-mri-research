# lumbar-spine-mri-research
Exploratory assessment of lumbar spine MRI datasets and existing machine learning and deep learning approaches, with a focus on research feasibility.
# Lumbar Spine MRI: Dataset Assessment and Research Feasibility Study

## Overview

This project focused on investigating the feasibility of conducting a machine learning-based research study using lumbar spine MRI data.

The work involved examining available spinal MRI datasets, analyzing their characteristics and annotation coverage, and conducting an extensive investigation of existing research approaches for automated spinal assessment. The objective was to understand the current state of research, identify limitations in the available data and existing methods, and determine whether a meaningful and achievable research direction could be established.

## Research Scope

The investigation covered three main areas:

- **Dataset Assessment:** Examining available lumbar spine MRI datasets, including their imaging characteristics, technical metadata, patient coverage, and annotation availability.
- **Existing Research Analysis:** Investigating published studies on automated lumbar spine MRI analysis, with particular attention to detection, classification, grading, and severity assessment of spinal conditions.
- **Research Feasibility:** Comparing existing approaches, identifying differences in datasets and evaluation methods, and assessing whether the available data could support a meaningful contribution beyond existing work.

## Dataset Investigation

The primary dataset examined in this project was the [Lumbar Spine MRI Dataset on Mendeley Data](https://data.mendeley.com/datasets/k57fr854j2/2).

It contains anonymized clinical MRI studies from 515 patients with symptomatic back pain, comprising 48,345 image slices in DICOM format.

The investigation examined:

- Axial and sagittal imaging views
- Image resolution and acquisition parameters
- DICOM metadata and technical characteristics
- Availability and scope of anatomical annotations
- Potential limitations of the dataset for different research tasks

A separate set of annotated axial MRI slices was also examined, containing labels for four anatomical regions relevant to lumbar spinal stenosis assessment.

## Analysis of Existing Approaches

Existing studies were investigated across two broad research categories:

**1. Detection and Classification**
- Intervertebral disc degeneration
- Disc herniation and bulging
- Lumbar spinal stenosis
- Other degenerative spinal conditions

**2. Grading and Severity Assessment**
- Disc degeneration grading
- Disc herniation grading
- Spinal stenosis severity assessment
- Measurement of anatomical structures relevant to spinal conditions

The investigation covered a range of machine learning and deep learning approaches reported in the literature, including CNN-based architectures, U-Net variants, ResNet, YOLO, Faster R-CNN, and other methods.

The reviewed studies were also examined in terms of dataset availability, annotation requirements, evaluation metrics, and reported performance.

## Key Findings and Project Outcome

The investigation highlighted several challenges affecting the feasibility of the proposed research:

- Existing studies covered a broad range of spinal MRI analysis tasks, with many already reporting promising results.
- Differences in datasets, imaging protocols, annotation methods, and evaluation metrics made direct comparisons between published results difficult.
- The available dataset and its annotations did not necessarily meet the requirements of all potential research directions.
- Reported performance on internal test sets did not always translate to comparable results on external datasets.

After evaluating the available data and existing approaches, the team concluded that, within its available resources and technical scope, it could not identify a sufficiently well-defined and achievable research direction that would support a meaningful contribution beyond existing work.

Consequently, the project concluded at the dataset assessment and research feasibility stage, before model development or training.

## Notes on the Research Materials

The accompanying report and literature review spreadsheet document the exploratory investigation conducted during the project.

The spreadsheet is intended as a working research resource rather than a finalized systematic review. Some bibliographic details, dataset information, and reported results may require further verification against the original publications.

The studies cover different datasets, tasks, and evaluation protocols; therefore, their reported performance metrics should not be interpreted as directly comparable.
