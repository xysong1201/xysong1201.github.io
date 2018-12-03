---
layout: post
title: "Freesurfer notes"
categories: [Study notes]
---

The .mgz file format is used to store high-resolution structural data and other data which are to be overlaid on the high-resolution structural volume.

* Freeview

With one Freeview command line, you can load several output volumes.

* Subcortical Segmentation
  * In automatic subcortical segmentation, each voxel in the normalized brain volume is assigned one of about 40 labels

  * The automatic subcortical segmentation can take many (11+) hours to complete.










## Freesurfer Tutorial
source: [link](https://www.youtube.com/watch?v=8Ict0Erh7_c)
### Parameters
* Input : T1 Weighted image
* T1 Contrast: white matter brighter than gray matter
* ~ 1 $$mm^3$$
* Higher resolution may be worse
* Full brain
* Usually one acquisition is ok
* More if high acceleration
* Siemens ---> MPRAGE or GE ---> SPGR
* 1,5T or 3T
* 7T might have problems
* Subject age > 5 years old
* Brain has no major problems (i.e. Tumours, Parts missing)
* Non-human primates possible





### Command Lines

### recon-all
Fully automated reconstruction, reconstruction here refers to cortical reconstruction.

* 1 T1 image ---> 180 slice of image. We call it series. recon-all use only one of those series, and it will find the other 179

#### -i
`recon-all -i file1.dcm -i file2.dcm`
* file.dcm is a single DICOM file
* you can use NIFTI as well with `-i file.nii`

#### -subject bert
"bert" is the name of the subject, also called subject ID. Freesurfer will create a folder and it will do all of its analysis inside of this folder. And it will go into great detail about what's inside of the folder.
Create a folder in $SUBJECTS_DIR

#### -all
means to do everything
can take 10-20 hours

inside the $SUBJECTS_DIR bert folder, there are 5 folders:
* scripts recon-all.log  recon-all.done
* mri : all the volume results
* surf : all the surface statistics
* label : all the surface statistics
* stats : table fits stats

.mgz > freesurfer specific format.
lh.orig: left hemisphere surface base file
rh.orig: right hemisphere surface base file

### Intensity Bias correction
When scan somebody, the brightness is not uniform across the image

### Skull skip
Remove all non-brain structure, --> brainmask.mgz

### White Matter Segmentation
wm.mgz
* Separates white matter from everything else
* Uses aseg to "fill in" subcortical structure
* Cerebellum removed, brain stem still there
