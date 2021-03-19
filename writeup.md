#### 1. Briefly state how you computed the camera matrix and distortion coefficients. Provide an example of a distortion corrected calibration image.

I calculated the chessboard corners on the pictures with cv2.findChessboardCorners(gray, (9,6), None) and then the and then the 3d points in real world, which are just points from x = 0-7 and y= 0-5 corner cordinates and z = 0 because it is a 2d plane and then called cv2.calibrateCamera that did the rest.
Then i did a perspective transform which only needs the source points which is the result of findChessboardCorners and the destination points are the points where I want the source points to be on the new picture.

#### 2. Describe how (and identify where in your code) you used color transforms, gradients or other methods to create a thresholded binary image.  Provide an example of a binary image result.

I used the soberl operator, gradiant magnitude, the direction of the gradient, and the hls color space to figure out which combination gives me the best result in finding lanes and then combined them.

#### 3. Describe how (and identify where in your code) you performed a perspective transform and provide an example of a transformed image.

I did this the same way as it was in the first point, so I just picked four points on the road as source points and just panned out the image, so as destination points I gave points on the corners of the image so it looks like the picture was taken from aove the road looking down.

#### 4. Describe how (and identify where in your code) you identified lane-line pixels and fit their positions with a polynomial?

I made a histogram along the columns and checked where the activations are, and where thosee activations are the highest value thats where the lanes are gonna be. I used those points as starting points and applied slinding windows cutting the image into 9 parts, I searched around the starting points and went up from there and fit a polynomial to those points.

#### 5. Describe how (and identify where in your code) you calculated the radius of curvature of the lane and the position of the vehicle with respect to center.

The camera is on the front of the car, so the car position will be the middle of the picture and I found out the middle of the lane position from the lanes and calculated the difference. Calculating the curvature I used the equation in the lesson.

final video: ./result_video.mp4