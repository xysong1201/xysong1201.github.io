---
layout: post
title: "Data format of MRI and the Python Analysis"
categories: [Study notes]
---
source:

[analyze 7.5](http://www.grahamwideman.com/gw/brain/analyze/formatdoc.htm)
[File format](https://analyzedirect.com/documents/AD_AnalyzeImage75_File_Format.pdf)
[Orientation and Voxel-Order Terminology](http://www.grahamwideman.com/gw/brain/orientation/orientterms.htm)

### Analyze 7.5 Format

__Mayo Clinic Analyze 7.5__ format is a file format for storing MRI data. An Analyze 7.5 data set consists of 2 files:
#### Header file(xxx.hdr):
Provides dimensional, identifying and some processing history information
#### Image file(xxx.img):
Consists of one long stream of voxel intensities, whose datatype and ordering are described by the header file.


### Orientation and Voxel-Order Terminology
* Directions are given relative to the patient.
* Right, Left, Anterior, Posterior, Inferior, Superior, Medial, Lateral

### MRI Image File Voxel ordering
A number of MRI file formats involve storing voxel intensities as simply a stream of intensity numbers in to a file in some agree-upon manner.
These formats require recording a number of characteristics of the image file, including voxel order, type of number used for intensity, and other attributes relating to conditions of image acquisition, processing steps that have been performed and so on.

#### Storage Order: R-L within P-A within I-S mean:
  * Voxels ordered from right to left to store a row
  * Rows ordered from posterior to anterior to store a slice
  * Slices stored from inferior to superior to store a volume|

#### Slice Orientation names
* Axial(Tranverse):R-L x A-P plane
* Coronal: R-L x S-I plane
* Sagittal: A-P x S-I plane


### Nibabel
A nibabel image is the association of three things:
* The image data array: a 3D or 4D array of image data
* An affine array that tells you the position of the image array data in a reference space
* image metadata describing the image, usually in the form of an image Header



a voxel is a pixel with volume

EPI slices displays the slices in grayscale


#### solve the problem of unalignment of the voxel coordinates in EPI and Anatomical Image

Keep track of the relationship of voxel coordinates to some __reference space__.
The *affine array* stores the relationship between voxel coordinates in the image data array and coordinates in the reference space.
