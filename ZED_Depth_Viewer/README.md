# ZED Depth Viewer

## Overview 

This application allows you to test out the ZED depth estimation software. Using the SDK, this app allows you to capture and display both the depth map and the 3D point cloud, and provides various viewing options. 

## Features
	
This section details the different features that come with the ZED Depth Viewer

### Available parameters

* Resolution : Set the desired image resolution, going from VGA to HD2K
* Frame rate : Choose at which framerate to sample the image, starting from 15 and up to 60 FPS. The framerate depends on the chosen resolution.
* View : Choose which camera feed, either left, right, or side-by-side, you which to view. 
* Measure : Choose which metric you which to visualize, either Depth or Confidence.
* 3D Point Cloud options :
  * LIDAR View : Enable LIDAR-type viewing
  * Depth Shading : Enable Depth Shading
  * Confidence 50 : Keep only the points for which the confidence is above 50%. If off, keep those with 100% confidence.
  * Texture 90 : Set the level of texturing to represent

### Depth Sensing Modes 

The ZED SDK provides two modes for depth sensing: *STANDARD* and *FILL*.

#### Standard Mode 
 
The STANDARD mode is the default depth sensing mode with the ZED. The STANDARD mode preserves distance metrics and shapes, and runs faster than the FILL mode, but it contains holes due to visual occlusions and filtering. These holes are represented by black areas in the depth image. Use the STANDARD mode for applications such as autonomous navigation, obstacle detection, 3D mapping, people detection and tracking.

#### Fill Mode

The FILL mode provides a fully dense depth map with a Z value for every pixel (X, Y) in the left image. The FILL mode fills holes and occlusions in the depth map and adds a filtering stage that improves edges and temporal stability but can alter the actual distance of objects in the scene.

This mode is recommended for applications such as mixed reality capture and visual effects. The FILL mode requires more resources and runs at a lower FPS than the STANDARD mode.

### Depth Modes

Several depth modes are available to fit your application’s needs. These settings adjust the level of accuracy, range and computational performance of the depth sensing module.

* **ULTRA**: offers the highest depth range and better preserves Z-accuracy along the sensing range.
* **QUALITY**: has a strong filtering stage giving smooth surfaces.
* **PERFORMANCE**: designed to be smooth, can miss some details.

Generally speaking, we recommend using the ULTRA mode for both desktop and embedded applications. If your application requires a lot of resources, switch to PERFORMANCE mode.

### Depth Range

Depth range corresponds to the minimum and maximum distance at which the depth of an object can be estimated. You can set both the minimum and maximum range using the `depth_minimum_distance` and `setDepthMaxRange()` parameters in `InitParameters`.
