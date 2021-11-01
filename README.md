# HA_OneControl
This project is meant to make things as easy as possible to integrate a Home Assistant instance with the Lippert OneControl system.
Using NodeRed, a connetion is made to the OneControl bridge, which is running OpenHab (read-only).  This connection sync's the OneControl state with an MQTT instance (I am using the official addon).  Once the connection is made, YAML files are used to create the devices within Home Assistant.


## High Level Overview ##

In certain Lippert OneControl implementations, there is the ability to interface with the control system from outside the proprietary CANbus architecture, and control components from external systems, such as home automation platforms.  The function that makes this possible it is the fact that they have implemented a read-ony instance of OpenHab as the functional bridge between the IP network provided by the wireless access point and the CANbus controller in the OneControl Touch Panel.  Because this OpenHab instance is read-only. no additional components can be added to the OpenHab controller, but API access is permuitted, and this is what I have been using.
