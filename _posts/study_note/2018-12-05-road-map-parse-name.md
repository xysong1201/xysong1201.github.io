---
layout: post
title: "Road map for Parsing Image data to PyTorch"
categories: [Study notes]
---

### Problem
Since the dataset consists of Analyze 7.5 format files. I want to find if there is already the software package to deal with the dataset.

### Trial

#### 1. Nibabel
First, I find the Nibabel
* Advantage: This package provides read +/- write access to some common medical and neuroimaging file formats, including: ANALYZE (plain, SPM99, SPM2 and later), GIFTI, NIfTI1, NIfTI2, MINC1, MINC2, MGH and ECAT as well as Philips PAR/REC.
* Disadvantage: it's too complicated without a clear representation for the plotting.

#### 2. Nilearn

* Advantage: Diverse plotting method.
* Suitable for dealing with Analyze 7.5 format.

#### 3. Pydicom
* A software package for dealing with DICOM files

#### 4. Nipype
Nipype consists of many parts, but the main ones are Interfaces, the Workflow Engine and the Execution Plugins.
[example](https://miykael.github.io/nipype_tutorial/notebooks/introduction_nipype.html#12)


Find [__BIDS__](http://bids.neuroimaging.io/): a simple and intuitive way to organize and describe neuroimaging and behavioral data.

#### 5. MedicalTorch
MedicalTorch is an open-source framework for PyTorch, implementing an extensive set of loaders, pre-processors and datasets for medical imaging. [link](https://medicaltorch.readthedocs.io/en/stable/)


### Conclusion
In the first step, __Nibabel__ and __Nilearn__ should be used in our project. And the __MedicalTorch__ will be useful in PytTorch.
