# CyberDog whole machine motion status sensing module

## **Introduction**
This module specifically implements the publisher whose topic is 'BodyState', and the server named cyberdog_body_state. The module inherits from `cyberdog_utils::LifecycleNode`.
BodyState reports two kinds of message data: posequat and speed_vector (posequat represents the attitude quaternion of the whole machine; speed_vector represents the instantaneous speed of the whole machine movement, unit: m/s)
The entire module communicates with the machine head stm32 through can and sensor in cyberdog_utils.
