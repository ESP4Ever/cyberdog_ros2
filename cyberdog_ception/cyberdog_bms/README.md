## Introduction to BMS module

The BMS module is the battery management module on Cyberdog and is mainly responsible for receiving and distributing battery information.
## The main function
* Receive BMS messages from the motion control panel through LCM. The messages mainly include
     *  battery power
     *  charging
     *  recharging current
     *Battery temperature
     *Battery health
     *Number of battery charge and discharge cycles
* As a ROS2 node, use ROS2 Service to provide BMS information to other nodes
     * Other nodes send requests to this module as Client
* Control head and tail LED lights according to charging status
     *Battery is low, LED flashes
     * During charging, the LED breathes
     * Charging is completed, LED is always on
* Play corresponding voice according to battery status
     * Play the current battery level when clicking the dog head
     * Voice announcement when battery is low
     * Announce the start of charging when charging starts
     * Announce shutdown volume
* Save charging information to the file system
* Save charging information to temporary file system

## Compile
Used colcon compilation system
* colcon build --merge-install --install-base /opt/ros2/cyberdog --packages-up-to cyberdog_bms

## document
* ./include/
     * bms_common.hpp
         * Common header files
     * time_interval.hpp
         * Class for checking time intervals
* ./src/
     * bms_recv.cpp
         * Receive LCM information from the bottom layer, convert and process the information, including sound control, lighting effect control, shutdown control, etc.
     * bms_logger.cpp
         * Date saving class
     * bms_control.cpp
         * LCM message sending class
     * bms_test.cpp
         * Test code
* ./CMakefile.txt
     * Compile script
* ./package.xml
     * Module declaration and dependency declaration
