# Final Deliverable

# **Sample Project**

Team: Nazari Tuyo (nazarituyo@brandeis.edu) and  (charliesquires@gmail.com

Date: COSI 119a Fall 2022, Brandeis University

Github repo: [https://github.com/campusrover/mini_scouter](https://github.com/campusrover/mini_scouter)

# **Introduction**

## **Problem Statement (including original objectives)**

If humans can’t enter an area because of unforeseen danger, what should be used instead? We created MiniScouter to combat this problem. The goal of our project was to create a robot that can be used to navigate or “scout” out spaces with directions coming from the Leap Gesture Controller or voice commands supported by Alexa. The robot takes in commands through hand gestures or voice, and interprets them. Once interpreted, the robot moves in the direction of the ****

## **Relevant Literature**

We referred to several documentations for the software used in this project:

[Boto3 Python Documentation](https://aws.amazon.com/sdk-for-python/)

[Boto3 Simple Queue Service Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html)

[Leap Motion Python SDK Documentation](https://developer-archive.leapmotion.com/documentation/python/index.html)

[Alexa Skill Developer Design Guide](https://developer.amazon.com/en-US/alexa/alexa-haus)

[Python Lambda Documentation](https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html)

[ROS Documentation](http://wiki.ros.org)

# **What was created**

We designed and created a voice and gesture controlled tele-operated robot. Voice control utilizes Alexa and Lambda integration, while gesture control is supported with the Leap Motion Controller.

## **Technical Description, illustrations**

### Leap Motion

Leap Motion Controller

![Untitled](Final%20Deliverable%2024e6a76061d34cb68f3866852d07deb9/Untitled.png)

The Leap Motion Controller is an optical hand tracking module that captures the movements of your hands. It can track hands and fingers within a 3D interactive zone and identify up to 27 different components in a hand. 

The controller use an infrared light based stereoscopic camera. It illuminates the space near it and captures the user’s hands and fingers. The controller then uses a tracking algorithm to estimate the position and orientation of the hand and fingers. The range of detection is about 150° by 120° wide and has a preferred depth of between 10cm and 60cm, but can go up to about 80cm maximum. The accuracy drops as the distance from the controller increases. 

![00308_psisdg9946_99460p_page_6_1.jpg](Final%20Deliverable%2024e6a76061d34cb68f3866852d07deb9/00308_psisdg9946_99460p_page_6_1.jpg)

The Leap Motion Controller maps the position and orientation of the hand and fingers onto a virtual skeletal model. The user can access data on all of the fingers and its bones. Some examples of bone data that can be accessed is shown below.

![00308_psisdg9946_99460p_page_7_1.jpg](Final%20Deliverable%2024e6a76061d34cb68f3866852d07deb9/00308_psisdg9946_99460p_page_7_1.jpg)

Alongside hand and finger detection, the Leap Motion Controller can additionally track hand gestures. The Leap Software Development Kit (SDK) offers support for four basic gestures:

- Circle: a single finger tracing a circle
- Swipe: a long, linear movement of a finger
- Key tap: a tapping movement by a finger as if tapping a keyboard key
- Screen tap: a tapping movement by the finger as if tapping a vertical computer screen

![00308_psisdg9946_99460p_page_8_1.jpg](Final%20Deliverable%2024e6a76061d34cb68f3866852d07deb9/00308_psisdg9946_99460p_page_8_1.jpg)

To start using the Leap Motion Controller, you’ll need to connect the device to your computer via a USB-A to Micro USB 3.0 cable. You’ll need to install the Leap software from their website at [https://developer.leapmotion.com/](https://www.leapmotion.com/setup/). We found that we had to install older versions of the tracking software as the latest versions (V4 and V5) only supported C and that the Python version had been deprecated. For our needs, V2 worked best

The Leap Motion Controller could not be connected directly to the robot so we set up a connection between the Leap Motion Controller and the computer. We used AWS boto3 to create an AWS Simple Queueing System (SQS) within the hello_robot.py file on the computer. Within the hello_robot.py file, we used the Leap Listener class to connect to the Leap Motion Controller and receive information such as number of hands, number of fingers, hand position, hand velocity, gestures, etc. This information is then put into a dictionary and sent to the queue as a string. Inside VNC, we have the hello_robot_vnc.py file that also implements a SQS using boto3. hello_robot_vnc.py receives the data through the SQS and converts the String messages back to a dictionary. We then use this data to set up teleop commands for the robot with hand gestures.

### Alexa Skills Kit

A widely known IOT home device, Amazon Alexa is Amazon’s cloud-based voice service, offering natural voice experiences for users as well as an advanced and expansive collection of tools and APIs for developer use. 

![Untitled](Final%20Deliverable%2024e6a76061d34cb68f3866852d07deb9/Untitled%201.png)

### AWS Simple Queue Service

## **Discussion of interesting algorithms, modules, techniques**

### Leap Motion Gestures

### Alexa Skill

### VNC

## **Guide on how to use the code written**

*** Mac OS ReadMe ****

****Create windows readme***

## **Clear description and tables of source files, nodes, messages, actions and so on**

MiniScout Package

|  |  |  |  |
| --- | --- | --- | --- |
|  |  |  |  |
|  |  |  |  |

# **Story of the project**

## **How it unfolded, how the team worked together:**

1. our initial idea
2. issues with leap and ROS
3. using AWS and working with the leap controller
4. adding voice control
5. vnc

## **problems that were solved, pivots that had to be taken**

1. dealing with ROS and Leap
2. lambda integration issues
3. windows/leap issues

## **Your own assessment**
