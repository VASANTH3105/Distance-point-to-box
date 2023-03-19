# Distance-point-to-box

![WhatsApp Image 2023-03-19 at 17 36 06](https://user-images.githubusercontent.com/122204153/226174068-a4d41092-a874-4b41-a1e8-29504a5805b0.jpg)


This is a Python program that uses the OpenCV library to capture video from a camera (specified by cap = cv2.VideoCapture(0)), and perform motion detection on the captured frames.

The program first captures two frames from the camera and flips them horizontally using the cv2.flip() function. These two frames are then used as the "previous" and "new" frames for motion detection.

In the while loop, the program calculates the difference between the "previous" and "new" frames using cv2.absdiff(). The resulting difference image is converted to grayscale using cv2.cvtColor() and smoothed with a 5x5 blur filter using cv2.blur().

The difference image is then thresholded using cv2.threshold(), with a threshold value of 10, to create a binary image that highlights areas of significant motion. The resulting binary image is then dilated using cv2.dilate() to fill in small gaps in the motion areas, and eroded using cv2.erode() to remove small noise.

The program then uses cv2.findContours() to detect contours in the binary image. Contours are used to identify the boundaries of the motion areas in the image. The program draws a circle on the "previous" frame to mark the starting position, and then iterates over each contour to identify motion areas larger than 30,000 pixels.

For each identified motion area, the program draws a rectangle around the area using cv2.rectangle(), finds the minimum enclosing circle using cv2.minEnclosingCircle(), and draws a line from the starting position to the center of the circle using cv2.line(). The program also adds text to the "previous" frame indicating the distance between the starting position and the center of the circle.

Finally, the program displays the "previous" frame with all of the motion detection visualizations applied using cv2.imshow(). The "new" frame becomes the "previous" frame, and a new frame is captured from the camera to become the "new" frame for the next iteration of the loop.

The loop continues until the user presses the Esc key (cv2.waitKey(1) == 27), at which point the program releases the camera and closes all OpenCV windows using cap.release() and cv2.destroyAllWindows().
