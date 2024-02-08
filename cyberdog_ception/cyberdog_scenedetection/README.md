#SceneDetection

This module provides scene detection function for the robot, obtains the current location information through the positioning chip, and determines whether the robot is currently indoors or outdoors through the satellite signal quality.

Accept the system's control commands for this module through the SceneDetection server, and publish the current location information to the system through the SceneDetection publisher.

## The main function

### SceneDetection server

- Receive control commands sent by the system. The command types are as follows:
   - Turn on positioning
   - Turn off positioning


### SceneDetection publisher

- Regularly (1S) publishes the current location information of the robot to the system, including the following content
- Longitude
- Latitude
- Scene discrimination results
	
- Filter non-essential positioning chip reporting information to reduce CPU usage

### other

* Complete positioning chip initialization
* Parse the data reported by the positioning chip

## Compile

Used colcon compilation system
* colcon build --merge-install --install-base /opt/ros2/cyberdog --packages-up-to cyberdog_scene_detection

## document

* ./src/
     *bream
         * Locate chip header file
     *hal
         * Locate chip header file
     * scene_detection.cpp
         * Implement SceneDetection server and SceneDetection publisher
     * patch_downloader
         * Locate chip header file
* lib_bream
     * Locate chip library
* ./CMakefile.txt
     * Compile script
* ./package.xml
     * Module declaration and dependency declaration
