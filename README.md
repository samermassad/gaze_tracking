# gaze_tracking
Simple gaze tracking in Python that uses an gradient-based algorithm by Timm & Barth to locate iris centers

## Algorithm
1. Localize centers of irises.
  1. Find faces in image.
  2. Get rough eye regions using hard-coded face proportions.
  3. Locate the iris center for each eye region.
    1. Compute x and y image gradients.
    2. Compute normalized gradient vector (g<sub>i</sub>) for each pixel. 
    3. Test each pixel as a possible center.
      1. Use each pixel's gradient vector.
        1. Compute normalized displacement vector (d<sub>i</sub>) from possible center to position of gradient vector.
        2. Compute dot product of (d<sub>i</sub>) and (g<sub>i</sub>), and add result to a sum for that possible center.
      2. If the sum for that possible center is greater than the previous max sum, store the coordinates of the possible center and update the max sum.
    4. Mark the coordinates for the possible center with the max sum as the center of that eye's iris.
2. Find reference points outside irises.
3. Compare iris centers with reference points to determine gaze direction.

## Timm & Barth's Eye Center Localization Algorithm
### Paper:  
Timm, F., & Barth, E. (2011, March). Accurate Eye Centre Localisation by Means of Gradients. In *VISAPP* (pp. 125-130).  
https://www.inb.uni-luebeck.de/fileadmin/files/PUBPDFS/TiBa11b.pdf 
### Demo:	
https://www.youtube.com/watch?v=aGmGyFLQAFM
