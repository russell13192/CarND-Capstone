# Capstone Project




This repository serves as the main repository for the Udacity Self Driving car Nanodegree program capstone project for the Localizers team. 

[//]: # (Image References)
[image1]: ./imgs/carla_architecture.png
[image2]: ./imgs/rosgraph.jpg
[image3]: ./imgs/system_architecture.png
[image4]: ./imgs/rosgraph.png

The members of team **Localizers**:
## Team Members

| Name                          | Slack handle | GitHub account                                    | Udacity Email                 |
|:------------------------------|:-------------|:--------------------------------------------------|-------------------------------|
| George Murray (team lead)  | @gmurray     | [russell13192](https://github.com/russell13192)         | gmurray@fetchrobotics.com   |
| Darrick Z                    | @darrick   | [darrickz]( https://github.com/darrickz)  | dz.aiml2018@gmail.com       |
| Hexuan Li                   | @LI Hexuan  | [rechuin]( https://github.com/rechuin)      | hexuan.li@hotmail.com          |
| Keisuke Shima                     | @Keisuke Shima        | [KeisukeShima](https://github.com/KeisukeShima)           | komaki289@gmail.com              |
| Ashish Reddy                      | @Ashish    | [abasired](https://github.com/abasired)         | bashish.iitg@gmail.com      |


The test vehicle for this project is the Udacity Self Driving car Carla. The cars modules and systems are displayed in the image below

![][image1]

Carla is broken into 3 main modules, Perception, Planning and Control which are all implemented via ROS. The architecture of the ROS stack is displayed below. 

![][image4]


The ROS modules are divided as follows :
 - `tl_detector` uses the camera to detect the traffic lights' color
 - `twist_controller` handles the control of the car
 - `waypoint_follower` makes sure the car follow the trajectory
 - `waypoint_loader` loads the route the car is going to follow
 - `waypoint_updater` adapts the car's route to the situation (eg. traffic light)

## Notes 

We ended up using tensorflow version 1.14.0 after some research online as to what the best version to use would be. We also made our runtime more stable by installing pyyaml(5.1.2) to proactive load the correct model based upon which launch file is used.

### (Original Udacity README)

Please use **one** of the two installation options, either native **or** docker installation.

This is the project repo for the final project of the Udacity Self-Driving Car Nanodegree: Programming a Real Self-Driving Car. For more information about the project, see the project introduction [here](https://classroom.udacity.com/nanodegrees/nd013/parts/6047fe34-d93c-4f50-8336-b70ef10cb4b2/modules/e1a23b06-329a-4684-a717-ad476f0d8dff/lessons/462c933d-9f24-42d3-8bdc-a08a5fc866e4/concepts/5ab4b122-83e6-436d-850f-9f4d26627fd9).

### Native Installation

* Be sure that your workstation is running Ubuntu 16.04 Xenial Xerus or Ubuntu 14.04 Trusty Tahir. [Ubuntu downloads can be found here](https://www.ubuntu.com/download/desktop).
* If using a Virtual Machine to install Ubuntu, use the following configuration as minimum:
  * 2 CPU
  * 2 GB system memory
  * 25 GB of free hard drive space

  The Udacity provided virtual machine has ROS and Dataspeed DBW already installed, so you can skip the next two steps if you are using this.

* Follow these instructions to install ROS
  * [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) if you have Ubuntu 16.04.
  * [ROS Indigo](http://wiki.ros.org/indigo/Installation/Ubuntu) if you have Ubuntu 14.04.
* [Dataspeed DBW](https://bitbucket.org/DataspeedInc/dbw_mkz_ros)
  * Use this option to install the SDK on a workstation that already has ROS installed: [One Line SDK Install (binary)](https://bitbucket.org/DataspeedInc/dbw_mkz_ros/src/81e63fcc335d7b64139d7482017d6a97b405e250/ROS_SETUP.md?fileviewer=file-view-default)
* Download the [Udacity Simulator](https://github.com/udacity/CarND-Capstone/releases).

### Docker Installation
[Install Docker](https://docs.docker.com/engine/installation/)

Build the docker container
```bash
docker build . -t capstone
```

Run the docker file
```bash
docker run -p 4567:4567 -v $PWD:/capstone -v /tmp/log:/root/.ros/ --rm -it capstone
```

### Port Forwarding
To set up port forwarding, please refer to the "uWebSocketIO Starter Guide" found in the classroom (see Extended Kalman Filter Project lesson).

### Usage

1. Clone the project repository
```bash
git clone https://github.com/udacity/CarND-Capstone.git
```

2. Install python dependencies
```bash
cd CarND-Capstone
pip install -r requirements.txt
```
3. Make and run styx
```bash
cd ros
catkin_make
source devel/setup.sh
roslaunch launch/styx.launch
```
4. Run the simulator

### Real world testing
1. Download [training bag](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/traffic_light_bag_file.zip) that was recorded on the Udacity self-driving car.
2. Unzip the file
```bash
unzip traffic_light_bag_file.zip
```
3. Play the bag file
```bash
rosbag play -l traffic_light_bag_file/traffic_light_training.bag
```
4. Launch your project in site mode
```bash
cd CarND-Capstone/ros
roslaunch launch/site.launch
```
5. Confirm that traffic light detection works on real life images

### Other library/driver information
Outside of `requirements.txt`, here is information on other driver/library versions used in the simulator and Carla:

Specific to these libraries, the simulator grader and Carla use the following:

|        | Simulator | Carla  |
| :-----------: |:-------------:| :-----:|
| Nvidia driver | 384.130 | 384.130 |
| CUDA | 8.0.61 | 8.0.61 |
| cuDNN | 6.0.21 | 6.0.21 |
| TensorRT | N/A | N/A |
| OpenCV | 3.2.0-dev | 2.4.8 |
| OpenMP | N/A | N/A |

We are working on a fix to line up the OpenCV versions between the two.
