# FaceSwapping
In this post I wrote a Python script to automatically replace facial features on an image of a face, with the facial features from a second image of a face.
The process breaks down into three steps:

A.  Detecting facial landmarks of two Images using Dlib landmark Detector: Dlib’s facial landmark or features detector is done on two parts, first detect face from the image and output rectangle of face detector and second landmark detector finds facial features inside the face rectangle  

2.  Face Alignment by Rotating, scaling, and translating the second image to fit over the first:The geometry of the two   faces are very different and so we need to warp the source face so that it covers the target face and use only Facial points on the outer boundary.

   i) Finding Convex Hull  of facial landmarks detected using dlib using cv2.convexHull(points, returnPoints = False)

   ii) Finding the Delaunay Triangulation of the points on the convex hull so that to warp corresponding areas of two different face based on the the facial landmark points.

   iii) Finding Affine warp triangles: An Affine warp triangle transforms a set of 3 points of a triangle to another set of arbitrary 3 points of triangle. It covers all above necessary requirements of translation rotation , scaling and translation

3. Blending and Adjusting the color balance in the second image to match that of the first: The difference in lighting and skin tone between the source and destination images makes the warped output image look unnatural. To overcome the difficulty, I used Seamless Cloning to copy an object from one image and paste it into another image making a composition that looks seamless and natural.  

