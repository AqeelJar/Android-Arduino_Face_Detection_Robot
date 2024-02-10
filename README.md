# Android Face Detection and Human Tracking Arduino Robot
Solution to project number 214 in the MATLAB and Simulink Challenge.

The solution uses an android device to detect and determine the position of a human face and then the android device sends the required response to the Arduino Uno robot to move the robot in the required direction to achieve a predefined distance between the robot and the human.

The solution uses simulink and matlab codes to detect and track the human face as well as controlling the Arduino Uno robot.

Please add the following items:

[Program link](https://github.com/mathworks/MATLAB-Simulink-Challenge-Project-Hub)

[Project description link]<Add link to the project description from the list of projects above>


# Project details
A description of the implementation and the approached adopted.

1. Generate a face dectection algorithm in simulink that can be used on an android device (samsung).
2. Control the Arduino Uno robot using a Serial Connection between the android and Arduino.
3. Control the Arduino Uno robot using a TCP/IP Connection between 2 android devices (since the Arduino Uno robot doesn't have built-in wireless communication signals to android device)
4. Face Detection on android device used to control Arduino Uno robot (wired or wireless connection is decided here)
5. Additional Codes for the Arduino Uno robot (Standalone)

# How to run section
Please explain step by step how to run the code/model and include information about what toolboxes and other resources needed to run it.

## Face Detection Application on Android Device
### Required Toolboxes or Software
* Simulink Support Package for Android Devices 
  * Android Studio (Arctic Fox 2020.3.1 Patch 4)
    * Android SDK Build Tools - 32.0.0
    * NDK (side-by-side) - 23.1.7779620
    * Android SDK Platform Tools - 32
  * Open CV Library - 4.5.2
  * ARM Compute Library - 19.05
* Computer Vision Toolbox
* C++ Compiler (preferably Microsoft Visual Studio compiler)
* Embedded Coder add-on
### Procedure

## Control Arduino Uno Robot with Android Device/s
### Required Toolboxes or Software
* Simulink Support Package for Arduino Hardware
* Embedded Coder
### Procedure

#### Serial Communication

#### TCP/IP Communication

## Arduino Uno Robot with Android Face Detection and Tracking
### Required Toolboxes or Software
* Simulink Support Package for Arduino Hardware
* Simulink Support Package for Android Devices 
  * Android Studio (Arctic Fox 2020.3.1 Patch 4)
    * Android SDK Build Tools - 32.0.0
    * NDK (side-by-side) - 23.1.7779620
    * Android SDK Platform Tools - 32
  * Open CV Library - 4.5.2
  * ARM Compute Library - 19.05
* Computer Vision Toolbox
* C++ Compiler (preferably Microsoft Visual Studio compiler)
* Embedded Coder add-on
### Procedure

## Additional Codes (Standalone Arduino)
### Required Toolboxes or Software
* Arduino IDE Software
* Libraries?

#### Obstacle Avoidance Robot

#### Line Following Robot

# Demo
Add a video or animated gif/picture to showcase the code in operation.
  
# References
Add reference papers, data, or supporting material that has been used, if any.
1. [Detect and Track Face on Android Device](https://www.mathworks.com/help/supportpkg/android/ref/detect-and-track-face-on-an-android-device.html)
2. [Controlling Elegoo Robot using Android Phone](https://www.youtube.com/watch?v=Tr4ih_EBk8c)
3. [TCP/IP Connection with Android Devices Example](https://www.mathworks.com/help/supportpkg/android/ref/connect-android-device-to-lego-mindstorms-ev3.html)
