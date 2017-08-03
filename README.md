![image001](https://user-images.githubusercontent.com/23239868/28748600-b190782c-7489-11e7-82ae-55db54c94050.jpg)
# Autonomous Snowmobile Monocular Obstacle Avoidance
*Lead Architect: Ryan J. Richards*

*LabVIEW and OpenCV code for obstacle detection and avoidance in snowy conditions*

![ezgif com-video-to-gif 4](https://user-images.githubusercontent.com/23239868/28676573-ff21a2be-72b8-11e7-88fa-b2b459883bd7.gif)

## Introduction/Methodology ##

Autonomous vehicles in snowy environments require an obstacle avoidance feature. Rather than using expensive equipment (LIDAR, sonar, etc),  a simple monocular solution can be created. This single-camera setup uses simple thresholding and particle analysis techniques to detect and highlight any obstacles. After detection, a steering avoidance script can be written to bypass the obstacle based on its location.

Although Optical-Flow based methods have been asserted in the past for monocular obstacle avoidance, a better algorithm involves color threshold and particle analysis - which takes advantage of the snow-covered environment. A feedforward image processing system has been created that has the following data flow:

![untitled diagram](https://user-images.githubusercontent.com/23239868/28692853-61054774-72f0-11e7-9c6b-1f76897dc23a.jpg)

Although the SnowDrone image processing unit was initially proposed to run on the Raspberry Pi (and send commands to the main ArduinoMEGA for obstacle avoidance), an alternative setup is to send images captured on the Raspberry Pi to the ArduinoMEGA, which would then relay the images back to the ground control station (GCS). The GCS would then processes the images on the main computer (therefore reducing power consumption, but also increasing processing time). Therefore, two options are proposed here (1) LabVIEW code which can easily be integrated into the GCS/GUI code and (2) Python code which utilizes OpenCV to be executed on the Raspberry Pi.

## LabVIEW Code ##



LabVIEW IMAQ (image acquisition) libraries [1] have been used extensively to complete the feedforward system (main image processing flow pictured below).

![1](https://user-images.githubusercontent.com/23239868/28693449-b45ea2ec-72f2-11e7-9ce3-2f288aeb96af.PNG)

This VI processes a video by taking individual pictures within a folder. You must convert the video to JPG/JPEG format before running it through this VI. Otherwise, modify the code to accomodate **.avi** videos.

You can control the delay of the code by adjusting the delay slide control - and stop the VI at any point by pressing the **stop** button.


![1](https://user-images.githubusercontent.com/23239868/28901534-c5667690-77c6-11e7-9ac9-4bd018751014.JPG)

## OpenCV/Python Code ##

This code has been proven to work on LabVIEW - but it must also be constructed on OpenCV using python so that it can be executed on a Raspberry Pi. 

## RaspberryPi/Camera Integration ##

## Testing/Results ##

![ezgif com-video-to-gif 2](https://user-images.githubusercontent.com/23239868/28652591-a7a80e5e-7256-11e7-9c03-d41bdddb1ac8.gif)

![ezgif com-video-to-gif 6](https://user-images.githubusercontent.com/23239868/28677336-38f9dc2a-72bb-11e7-8e94-b41546a17c08.gif)


## Appendix ##

[1] http://www.ni.com/white-paper/3470/en/


