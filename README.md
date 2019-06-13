# Supplementary_Code_SolidEarth 
This repository contains MATLAB scripts that implement a method to extract digitized fractures from images of fractured rocks. The method 
is described in the manuscript titled ,"An automated fracture trace detection technique using the complex shearlet transform"(se-2019-104)
that is submitted to Solid Earth Journal (https://www.solid-earth.net/). 

The files in this repository consists of four MATLAB scripts that perform the following functions:
  1. Ridge_Ensemble_Generator.m 
                                -> creates a set of shearlet systems based on user-defined ranges and saves them as *.mat files
                                -> reads a set of images of fractured rocks
                                -> computes a number of ridge realizations based on a user-defined range of ridge extraction parameters
                                   and adds the detected ridges into a single image and saves it. This is referred to as ridge ensemble.
  2. Ridge_Ensemble_Reader.m 
                                -> reads the ridge ensemble image and applies a non-linear, sigmoid function in order to filter away 
                                   possible false positives and retain probable fracture ridges, by means of a user-defined threshold
                                -> saves the highly probable, fracture ridge map as a binarized image                               
  3. Ridge_Post_Processing.m
                                -> reads the binarized ridge image files
                                -> performs a segmentation operation using Otsu thresholding that removes isolated and very small pixel
                                   clusters
                                -> skeletonizes the ridge clusters into thinned pixel reresentations preserving the branch points
                                -> fits polylines to the skeletonized ridge clusters and saves as tables (*.mat files) 
  4. Polyline_to_Shape.m   
                                -> converts the polylines into shape files
                                -> georeferences the polylines (if georeferencing information is available)
                                -> performs rotation, scaling, and translation of polylines (if necessary)
                                -> performs line simplification of polylines using the Douglas-Peucker algorithm (if necessary)
                                -> converts polylines into shapefiles structures and saves as shapefiles
