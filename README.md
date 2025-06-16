# Pre-Processing-Pipeline

Pre Processing Pipeline
By-Syed Reebal Faakhir Andrabi

Some preprocessing techniques I have learnt in the duration of this project and which I implemented to pre process mri images are as follows:-

Initially I defined a simple image plotting function which takes two images and plots the same. I also defined a get middle slice function which extracts the middle slice from a 3-D image along a specified axis which as default was set to get axial view.
1.	Skull Striping:-
It is a preprocessing technique in medical image analysis, it removes non-brain tissue such as fat, skull, scalp and eyes from the image leaving only the required regions for analysis.
It was employed using HD-BET which was actually a project, the information and code and application can be found on github at (https://github.com/MIC-DKFZ/HD-BET).

2.	Resampling using Torchio:-

Torchio is an open-source pyhton library which is specifically designed for preprocessing of mri images. I came across the same through a research paper by Fernando Garcia (https://www.sciencedirect.com/science/article/pii/S0169260721003102). It employs several techniques for the preprocessing of mri images specially. One of these is resampling, it changes voxel spacing i.e it produces standardised input which is optimum for training of our models. 

3.	CropOrPad:-
It is another technique in Torchio. It basically removes voxels from the edge of the images and adds zeroes(corresponding to intensity) in their stead.

I implemented as standard using a subject object and then applying the required transformations on it. Here I employed the forementioned techniques also and in addition used np.flip to get the right orientation of the image as I found the image to be upside down earlier. 

4.	ToCanonical:-
It converts the image orientation to a canonical axis order (RAS: Right-Anterior-Superior) and thus ensures all images follow a consistent coordinate system.

5.	Z-Normalisation:-

It standardises the image intensities to mean=0 and std=1 and helps neural networks to converge faster.
6.	Other Data-Augmentation Techniques:
These include techniques such as random affine(translation, rotation and scaling), random elastic deformation(applies deformations), random flip, random anisotropy( which makes resolutions to differe along axes), random noise, random blur and random gamma help prevent overfitting of model. 

7.	CLAHE(Contrast Limited Adaptive Histogram Equalization):
It is an adaptive Histogram normalization technique, where local contrast is adjusted instead of global contrast. The image is divided into small disjoint chunks and then histogram Equalization is applied to each chunk. This method is helpful when the lightening condition oven an image is not uniform.
8.	Thresholding:-
Thresholding is a technique used to segment an image by converting it from grayscale to binary (black and white). It helps separate objects (foreground) from the background based on pixel intensity values.
Simple thresholding uses a fixed threshold value for the whole image whereas adaptive threshold uses different values for different regions of the image.
9.	Gaussian Blur and Morphological Operations:
These are originally meant for rgb images and not dull greyscale images. Thus they didn’t produce good results.



