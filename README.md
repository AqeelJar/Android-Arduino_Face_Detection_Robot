# Face Detection and Human Tracking Android-Arduino Robot
Solution to project number 214 in the [MATLAB and Simulink Challenge](https://github.com/mathworks/MATLAB-Simulink-Challenge-Project-Hub).

Project Title: [Face Detection and Human Tracking Robot](https://github.com/mathworks/MATLAB-Simulink-Challenge-Project-Hub/tree/main/projects/Face%20Detection%20and%20Human%20Tracking%20Robot#project-description)
## Problem Description 
Human-robot interaction is crucial in many computer vision applications, such as activity identification, automobile safety, smart home security applications, and surveillance. A robot's job is to be an efficient assistant to aid humans with their tasks. The robot must be proficient in communicating with and interacting with people. In this situation, the main requirement for the vision system in this type of robot is a human face-tracking system. Robotic human-robot interaction can be improved via face detection. Detecting and tracking humans automatically using a sensor or algorithm is a difficult problem due to the wide variety of positions, and system complexity. It is, ultimately, a detailed optimisation problem.

Therefore, a low-cost, user-friendly, and real-time autonomous human tracking robot using an Android mobile was put into action. The human tracking is done by a face detection Simulink model on the Android device while the real-time control is done by an Arduino Uno Controller. The face detection model was designed using the Computer Vision Toolbox and Deep Learning Toolbox on Simulink. The hardware support packages are used to interface and deploy the Android and Arduino devices with Simulink models. The different types of connection available between the Android device and Arduino Uno controller were also taken into consideration. The Android device was able to run the face detection algorithm and send the required information to the Arduino Controller to control the movements of the robot to achieve a predefined distance between the robot and the human. Therefore, a deep learning-based face detection and tracking Robot was developed.

# Project details

1. A face-detection Simulink model was deployed on an Android device. The position of the detected face is used to determine the midpoint of the detected face and the maximum area that the detected face should be to achieve a predefined distance between the camera and the detected face. Using the above information, a response algorithm can be modelled using a MATLAB function in Simulink. This function would be able to determine whether the camera should move forward, turn right, turn left, move back or stop based on the position and area of the detected face in the video frame.

2. Control the Arduino Uno robot using an input response signal. Before using the Simulink models on the Arduino Uno robot, the performance of the robot was tested using the Line Tracking Code and Obstacle Avoidance code using the Arduino IDE software and was deemed acceptable to use for the project. The Arduino Uno robot should be controlled using an input response signal coming from the Android device or computer. To achieve this, a switch-case block in Simulink is used to read the input signal and determine which digital pin signal configuration should be sent to the motors to achieve a specific motion. The speed can also be changed based on the amount of voltage sent to the motor control module. This is also modelled using Simulink. The input response signal can only be communicated via a serial connection to the Arduino Uno board.

3. Communication between the Android device and Arduino Uno robot. Two connection types were investigated. The TCP/IP connection between Android devices and the direct serial connection. A button control application is developed to test both connections to see if there are any faults when using both connections. The application allows the user to press a response from the Android display and send out the response via the connection type. The application has a safety feature that causes the robot to stop when more than one button is pressed. Both connections showed impressive response times. Each connection type is best under different applications. In terms of the Button Control Application, the TCP/IP connection is the optimal connection type as the user can move independently from the robot. However, in terms of the face detection application, the direct serial connection would be the optimal connection type as the device would be attached to the robot and is expected to move with the robot.
   - The **direct serial connection** allows the Android device to be connected to the Arduino robot using a type-C to USB converter and USB cable. The Button Control Application was deployed on the Android device with a serial send connection block. This connection type is considered a wired connection and constrains the motion of the robot to the length of the wire. The user is expected to move with the robot.
   - The **TCP/IP connection** allows the first Android device (server) to send out an input response signal using the Button control application with a TCP/IP send block in Simulink. A second Android device (client) receives the input response signal using a TCP/IP receive block and sends out the signal using a direct serial connection. This connection was developed due to the Arduino Uno having no wireless connection modules that can be used on Simulink to connect to the Android device. The second Android device would be fixed to the Arduino robot and the first Android device would be with the user. This allows the user to be in one position while the robot moves in different positions. Both Android devices are expected to be on the same Wi-Fi network to achieve this connection. If the Wi-Fi network is busy, then the robot will respond with a delay or time lag. Thus, it is suggested to use a private and controlled Wi-Fi network.
  
4. Using modified the face detection model and the Arduino robot model, the final face detection and tracking Arduino robot model can be deployed. The Android device would need to be attached to the Arduino robot. Thus, a selfie stick with a couple of elastic bands and cable ties allows the Android device to be placed high enough to detect a face without causing the Android device to fall. A ballast was also used to counteract the lever weight due to the selfie stick and phone. The mass of the ballast can be modified to achieve enough friction on the wheels to move the robot at a controlled speed to allow the face detection algorithm to detect a face in each video frame. This allows the robot to move towards the human when they change their location.

5. The face detection and tracking robot can keep a predefined distance between the camera and the detected face using the Simulink models for the Android device and Arduino Uno board that was explained above.


# How to run section
Before following the How to run section for each application, it was assumed that all the [Required Hardware](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/edit/main/README.md#android-face-detection-and-human-tracking-arduino-robot) were assembled and ready to use and it was also assumed that all the [Required Toolboxes and Software](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/README.md#required-toolboxes-and-software) were installed. The list below shows all the applications used to solve the problem.

1. [Face Detection Application on Android Device](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#face-detection-application-on-android-device)
2. [Control Arduino Uno Robot with Android Device/s](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#control-arduino-uno-robot-with-android-devices)
   - [Arduino Uno Controller](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#arduino-uno-controller-controlarduinorobotslx)
   - [Direct Serial Communication](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#direct-serial-communication-buttoncontrolappslx)
   - [TCP/IP Communication between Android Devices](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#tcpip-communication-between-android-devices)
4. [Arduino Uno Robot with Android Face Detection and Tracking](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/tree/main#arduino-uno-robot-with-android-face-detection-and-tracking)

## Required Hardware
* 1-2 Android Devices
* [USB to Type-C Data & Fast Charging Cable](https://www.takealot.com/usb-to-type-c-data-fast-charging-cable-for-samsung-1m/PLID73135642)
* [Elegoo Arduino Uno Robot Car Kit V3.0](https://www.elegoo.com/products/elegoo-smart-robot-car-kit-v-3-0-plus)
* 2x[Rechargeable Battery - 18650 - 4200mAH](https://www.takealot.com/rechargeable-battery-18650-4200mah/PLID57464670)
* [USB to type-C converter](https://www.takealot.com/innovatex-usb-3-0-to-type-c-adaptor-transfer-speeds-up-to-5gbps-/PLID93523584)
* [Serial Connection Cable](https://www.takealot.com/hq-usb-2-0-a-to-b-3-0m-hp-canon-lexmark-printer-cable/PLID71037965?gad_source=1&gclid=CjwKCAiA_aGuBhACEiwAly57MeJWeZzAQiE4Sr9q8wg4TXOIqfKfltW6FqdJqaUklDWqF5TO4Fw-OhoC8kAQAvD_BwE&gclsrc=aw.ds)
* Selfie Stick (Attach phone to Arduino robot)

## Required Toolboxes and Software
* [MATLAB R2023a](https://www.mathworks.com/products/new_products/release2023a.html)
* [Simulink Support Package for Arduino Hardware](https://www.mathworks.com/matlabcentral/fileexchange/40312-simulink-support-package-for-arduino-hardware)
* [Simulink Support Package for Android Devices](https://www.mathworks.com/hardware-support/android-programming-simulink.html) 
  * [Android Studio (Arctic Fox 2020.3.1 Patch 4)](https://developer.android.com/studio/archive)
    * Android SDK Build Tools - 32.0.0
    * NDK (side-by-side) - 23.1.7779620
    * Android SDK Platform Tools - 32
  * Open CV Library - 4.5.2
  * ARM Compute Library - 19.05
* [Computer Vision Toolbox](https://www.mathworks.com/products/computer-vision.html)
* [Deep Learning Toolbox](https://www.mathworks.com/products/deep-learning.html)
* [C++ Compiler (preferably Microsoft Visual Studio compiler)](https://visualstudio.microsoft.com/vs/features/cplusplus/)
 * [Choose a compiler in MATLAB](https://www.mathworks.com/help/matlab/matlab_external/choose-c-or-c-compilers.html)
* [Embedded Coder add-on](https://www.mathworks.com/products/embedded-coder.html)
* [Arduino IDE Software with relevant driver installations](https://www.arduino.cc/en/software)

## Face Detection Application on Android Device 

### Android Device ([FaceDetectionApp.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Face%20Detection%20App/FaceDetectionApp.slx))
1. Launch the Simulink model on MATLAB.
2. Connect the Android device to the computer.
3. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows Android Device and make sure that the connected Android device is visible under the device options in the target hardware resources setting. 
4. In the Face detection and Tracking Block, open the Android camera block properties and select the back camera with a pixel size of 384x384.
5. Build, Deploy and Start the Simulink model on the Android device.
6. After deploying the application on the android device, allow all permissions that are shown on the android display screen.
7. Ensure that the phone is rotated 90 degrees counterclockwise such that the phone is in a landscape position. The face detection algorithm only works in this position.
8. Ensure that the coordinates of the corner points are of expected values.

## Control Arduino Uno Robot with Android Device/s

### Arduino Uno Controller ([ControlArduinoRobot.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/ContolArduinoRobot.slx))
1. Launch the Simulink model on MATLAB.
2. Connect the Arduino Uno robot to the computer.
3. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows Arduino Uno. If the port number of the connected Arduino Uno board is known, the number can be manually inputted under the Host COM port found in the Target hardware resources under the Host-Board connection.
5. Build, Deploy and Start the Simulink model on the connected Arduino Uno board.
6. After deploying the robot would have the required program to control the motors, but the type of communication between the Android device and Arduino robot needs to be established and both communication types do not affect the programming of the control of the Arduino robot.

#### Direct Serial Communication ([ButtonControlApp.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/Direct%20Serial%20Communication/ButtonControlApp.slx))
1. Launch the Simulink model on MATLAB.
2. Connect the Android device to the computer.
3. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows the Android Device and make sure that the connected Android device is visible under the device options in the target hardware resources setting.
4. Build, Deploy and Start the Simulink model on the connected Android Device.
5. After deploying the application on the Android device, allow all permissions that may show on the Android display screen.
6. Connect the Android device to the Arduino robot using the USB cable and USB to type-C convertor.
7. Ensure that the USB connector is connected which is shown in the notification tab on the Android device.
8. Ensure that the battery pack is turned on.
9. Test out the connection by pressing any of the displayed buttons on the display screen.
10. If no movement is shown but noise is coming from the board, either the batteries are low or the CarSpeed variable is too low. Modify the ControlArduinoRobot model and increase the CarSpeed to any value not more than 255 then follow the same steps to deploy the ControlArduinoRobot model on the Arduino robot. The steps for the communication type don't need to be repeated.
11. Play around with the wired Arduino Uno robot.



#### TCP/IP Communication between Android Devices 
##### Both Android Devices ([ButtonControlApp_Client.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Client.slx)) ([ButtonControlApp_Server.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Server.slx))
1. Make sure that both Android devices are connected to the same Wi-Fi network.
2. Once both Android devices are connected, one Android device will be the server device (First Android Device) and the other will be the client device (Second Android Device). The IP address of the server would need to be known. This can be found under the connected Wi-Fi settings on the Android device or if the FaceDetectionApp model was deployed on the device the IP address can be found in the Info tab while using the application. Write down or memorise the IP address of the server.
3. Launch both Simulink models on MATLAB.
4. If there are enough ports on the computer, connect both Android devices to the computer. If not, then connect one device at a time when deploying the different Simulink models.
5. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows the Android Device.


##### First Android Device ([ButtonControlApp_Server.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Server.slx))
6. In the hardware settings, make sure that the First Android Device is visible under the device options in the target hardware resources setting.
7. Make sure that the TCP/IP send block is in server mode with a port number of 25000. This number should match the client port details on the Second Android Device.
8. Build, Deploy and Start the Simulink model on the First Android Device.
9. After deploying the application on the Android device, allow all permissions that may show on the Android display screen.


##### Second Android Device ([ButtonControlApp_Client.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Client.slx))
10. In the hardware settings, make sure that the Second Android Device is visible under the device options in the target hardware resources setting.
11. Make sure that the TCP/IP receive block is in client mode with a port number of 25000 (same as the server) and that the Remote IP address matches the server's IP address. Also, make sure that the data type is set to uint8.
12. Build, Deploy and Start the Simulink model on the First Android Device.
13. After deploying the application on the Android device, allow all permissions that may show on the Android display screen.


##### Both Android Devices ([ButtonControlApp_Client.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Client.slx)) ([ButtonControlApp_Server.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20Control/TCP-IP%20Communication/ButtonControlApp_Server.slx))
14. After deploying both Simulink models on their corresponding Android Devices, make sure the TCP/IP connection is connected under the Log tab on both Android Devices.
15. Connect the second device to the Arduino robot using a USB cable and USB to type-C converter and attach the Second Android Device to the Arduino robot such that the Android Device would not fall off when the robot begins to move.
16. Ensure that the USB connector is connected which is shown in the notification tab on the second Android device.
17. Ensure that the battery pack is turned on.
18. Test out the TCP/IP connection between Android Devices by pressing any button displayed on the First Android Device's display and the corresponding response signal should be shown in the Second Android Device's display.
19. If no movement is shown but noise is coming from the board, either the batteries are low or the CarSpeed variable is too low for movement. Modify the ControlArduinoRobot model and increase the CarSpeed to any value not more than 255 then follow the same steps to deploy the ControlArduinoRobot model on the Arduino robot. The steps for the communication type don't need to be repeated.
20. The Arduino robot with the Second Android Device should move independently from the First Android Device (wireless connection).
21. Play around with the wireless Arduino Uno robot.


## Arduino Uno Robot with Android Face Detection and Tracking

### Android Device ([FaceDetectResponseApp.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20with%20Android%20Face%20Detection/FaceDetectResponseApp.slx))
1. Launch the Simulink model on MATLAB.
2. Connect the Android device to the computer.
3. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows the Android Device and make sure that the connected Android device is visible under the device options in the target hardware resources setting. 
4. In the Face Detection and Tracking Block, open the Android camera block properties and select the back camera with a pixel size of 384x384.
5. Build, Deploy and Start the Simulink model on the Android device.
6. After deploying the application on the Android device, allow all permissions that are shown on the Android display screen.
7. Ensure that the phone is rotated 90 degrees counterclockwise such that the phone is in a landscape position. The face detection algorithm only works in this position.
8. Ensure that the coordinates of the corner points are of expected values.
9. Ensure that the response signals are to the expected values. This is done by following the response signal displayed on the Android screen when a face is detected. This should allow the camera/phone to stop at a predefined distance away from the detected face. The descriptions of the response signals are noted below:
   - Stop = 0
   - Forward = 1
   - Reverse = 2
   - Right = 3
   - Left = 4
### Arduino Uno Controller ([ControlArduinoRobot.slx](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Arduino%20Uno%20Robot%20with%20Android%20Face%20Detection/ContolArduinoRobot.slx))
1. Launch the Simulink model on MATLAB.
2. Connect the Arduino Uno robot to the computer.
3. In the Hardware tab, select hardware settings and make sure that the connected hardware board shows Arduino Uno. If the port number of the connected Arduino Uno board is known, the number can be manually inputted under the Host COM port found in the Target hardware resources under the Host-Board connection.
5. Build, Deploy and Start the Simulink model on the connected Arduino Uno board.
6. After deploying the Simulink model, attach the selfie stick to the Robot by pushing one end into the top back hole of the robot and allowing the stick to lean forward.
7. Fix the lean angle of the selfie stick with elastic bands that are attached to the front part of the robot.
8. Attach the Android device to the selfie stick to achieve an appropriate height away from the ground.
9. Connect the Android device to the Arduino Robot using the USB cable and USB to type-C convertor.
10. Ensure that the USB connector is connected which is shown in the notification tab on the Android device.
11. Ensure that the battery pack is turned on.
12. Add a customizable ballast on the battery pack to counteract the front centre of gravity that is produced due to the weight of the phone. The ballast would have a container that can allow the weight to be changed by adding or removing coins.
13. Allow the back wheels to have less friction than the front wheels by fine-tuning the weight of the ballast. This should allow the vehicle to move at a controlled speed to allow the face to be detected more easily and accurately. This calibration can be done using the ButtonControlApp Simulink model when calibrating specific movements.
14. Test out the Face detection Android-Arduino robot in a well-lit area and in the same place where the calibration was done as different grounds would have different coefficients of friction and would cause the robot to either slow down or speed up.
15. Once a face is detected, test the robot by moving the face left and right and see if the robot would move with the face.
16. Once the robot stops at the predefined distance, move the face closer to see if the robot would move back to keep the distance between the phone and the detected face constant.
17. Play around with the Face Detection and Tracking Android-Arduino Uno robot.

# Demo
1. [Face Detection App](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Videos/FaceDetectionApp.mp4)
2. [Button Control with Direct Serial communication](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Videos/ButtonControlApp%20-%20Direct%20Serial.mp4)
3. [Button Control with TCP/IP Communication between android devices](https://github.com/AqeelJar/Android-Arduino_Face_Detection_Robot/blob/main/Videos/ButtonControlApp%20-%20TCP-IP.mp4)
4. [Arduino Uno Robot with Android Face Detection and Tracking](Link)
  
# References
1. [Detect and Track Face on Android Device](https://www.mathworks.com/help/supportpkg/android/ref/detect-and-track-face-on-an-android-device.html)
2. [Controlling Elegoo Robot using Android Phone](https://www.youtube.com/watch?v=Tr4ih_EBk8c)
3. [TCP/IP Connection with Android Devices Example](https://www.mathworks.com/help/supportpkg/android/ref/connect-android-device-to-lego-mindstorms-ev3.html)
