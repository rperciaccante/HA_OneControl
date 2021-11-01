# HA_OneControl
This project is meant to make things as easy as possible to integrate a Home Assistant instance with the Lippert OneControl system.
Using NodeRed, a connetion is made to the OneControl bridge, which is running OpenHab (read-only).  This connection sync's the OneControl state with an MQTT instance (I am using the official addon).  Once the connection is made, YAML files are used to create the devices within Home Assistant.


## High Level Overview ##

In certain Lippert OneControl implementations, there is the ability to interface with the control system from outside the proprietary CANbus architecture, and control components from external systems, such as home automation platforms.  The function that makes this possible it is the fact that they have implemented a read-ony instance of OpenHab as the functional bridge between the IP network provided by the wireless access point and the CANbus controller in the OneControl Touch Panel.  Because this OpenHab instance is read-only. no additional components can be added to the OpenHab controller, but API access is permuitted, and this is what I have been using.

During normal operations, Node Red subscribes to the official OpenHab event API, and syncronizes actions observed in the OpenHab environment with MQTT.  The official OpenHab APIs are then used to push changes back from MQTT to OpenHab.

### Components Used - Software ###
1. ** Node-Red ([https://nodered.org/](https://nodered.org/)) **
  - Because I am using Home Assistant as my automation platform, I am using the official Node Red add-on
  - Node Red can be installed onto just about any platform - see link above
  - The following Node Red nodes have been added to the default node set:
    - node-red-contrib-sse-client ([https://flows.nodered.org/node/node-red-contrib-sse-client](https://flows.nodered.org/node/node-red-contrib-sse-client))
2. ** Mosquitto MQTT broker ([https://mosquitto.org/](https://mosquitto.org/)])**
  - Because I am using Home Assistant as my automation platform, I am using the official MQTT broker add-on
  - Mosquitto can be installed onto just about any platform - see link above.
3. ** Home Assistant ([https://www.home-assistant.io/](https://www.home-assistant.io/))**
  - Incredibly powerful and flexible automation platform

** Please note **
This project focuses on Home Assistant as the automation platform as a matter of personal perference, however, the Node Red flows sync with MQTT, meaning that any other platform capable of publishing and subscribing to MQTT could be adapted to use this process.

## How To ##

1. Install Node Red according to the instruction on their website.  Follow instructions in the node_red section above.
2. If you are using Home Assistant, follow the instructions in the home_assistant section above.
