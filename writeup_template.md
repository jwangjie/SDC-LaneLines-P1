# **Finding Lane Lines on the Road** 

### Reflection

An OpenCV based vision pipeline was developed for detecting lane lines and then drawing averaged boundary lines in the road videos. The pipeline can be developed and tested by the images in the "test_images" first. Then videos in the "test_videos" folder can be processed. In the pipeline development, color selection, Gaussian blurring, Canny edge detection, region of interest selection, and Hough transform line detection techniques were used. The pipeline development process is summarized as follows:

1. White and yellow colors detection: cv2.inRange, cv2.bitwise_or, cv2.bitwise_and
2. Apply Grayscale transform: cv2.cvtColor()
3. Apply Gaussian Smoothing: cv2.GaussianBlur()
4. Apply Canny Edge Detection: cv2.Canny()
5. Define Region of Interest Selection: cv2.fillPoly()
6. Conduct Hough Transform line detection: cv2.HoughLinesP()
7. Draw two averaged lines: cv2.line()
8. Draw the lines in the video: VideoFileClip()

The built pipeline works fine for straight white and yellow line detections, but doesn't work for curved lines. This is due to the fact that the used "draw_lines()" method assuming the lane lines were linear. Moreover, even replacing the line drawing method, the "region_of_interest()" may loss normal functions for the steep roads.

In order to work for the curved and steep road lane detections, more advanced and adaptive region of interest selection technique need to be applied.
