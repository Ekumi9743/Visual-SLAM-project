## Summary Report
  
In step 2, I will create a dataset about one scene of my choice. In this part, I will first replace the dataset in step 1 and run the images I need to process in SLAM. Use the sample provided, reconstruct the scene from image, predict and camera trajectory. Just like the the Visual-SLAM, the SLAM will initialize the map that holds 3-D world points, after the correspondences are found, two geometric transformation models are used to establish map initialization. After the map is initialized using two frames, you can use "imageviewset" and "worldpointset" to store the two key frames and the corresponding map points.

Then the SLAM will loop detection by using the bags-of-words approach. Refine the initial reconstruction using "bundleAdjustment", that optimizes both camera poses and world points to minimize the overall reprojection errors. The tracking process is performed using every frame and determines when to insert a new key frame. For Local mapping, it is performed for every key frame. When a new key frame is determined, add it to the key frames and update the attributes of the map points observed by the new key frame.

The loop closure detection step takes the current key frame processed by the local mapping process and tries to detect and close the loop. Loop candidates are identified by querying images in the database that are visually similar to the current key frame using evaluateImageRetrieval. You can compare the optimized camera trajectory with the ground truth to evaluate the accuracy of ORB-SLAM.

After all the steps, we can get the final output. We can compare the final output with step 1 to determine its feasibility.

