
To encourage people to solve the challenges related to autonomous driving many Open-Source
Autonomous Driving Datasets have been proposed. One such dataset is also contains phone GPS,
thermometers and 9-axis IMU. This dataset is commonly know as Comma2K19 dataset and can be
downloaded from https://github.com/commaai/comma2k19. Additionally, the EON captures raw
GNSS measurements and all CAN data sent by the car with a comma grey panda. Our goal is not
to solve the mapping of scene information on a global top-view (ortho-rectified or satellite) to
provide an overall understanding of the route.
Task 1: Ground Segmentation
1. Apply any segmentation algorithm to segment the ground/lanes
Task 2: Top-view Generation
Manually compute the projection of ground plane to top-view. Using GPS Coordinates locate the
part of the data you are working on and compute a homography to map the first frame of the
video to the top-view/satellite image. Use a reference object to scale the top-view
Task 3: Projection of Entire Video on Top-view
Use Super Glue to find a homography between n-th image to 1st image. Use the first image to
top-view projection to project the object on the top-view. The will result in a progressive
generation of a top-view of the highway.
https://github.com/bimalka98/Stitch-images-using-SuperGlue-GNN

Task 4: Visualise Object Detection on Orthographic Top-View
Perform object detection using any standard object detector such as YOLO and visualzie the
result on the dash cam video i.e. raw video. Then overlay detection locations (i.e. mid-point of
base of bounding box) on top-view/satellite view. Object detector will give you a list of bounding
boxes, note the mid-point of the base of bounding box and project it on to the top view/satellite
view using the computed homography sequence (current view to first image, first image to
satellite image).

Task 5: Visualize the Generated top-view with object detection on Google Earth.
Open the Google Earth Pro software and overlay the generated top-view of highway on the satellite
image. Analyse whether the generated top view is correct or not. Use IMU and GNSS data to
improve the results i.e. to remove the accumulating error due to projection of each frame onto the
first frame.
Task 6: Bonus (5%)
5.1 Run your entire system on a video recorded by yourself via dashcam
5.2 Run you system on a live feed from a dasocam video.
