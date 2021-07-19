# HA_OneControl
This project is meant to make things as easy as possible to integrate a Home Assistant instance with the Lippert OneControl system.
Using NodeRed, a connetion is made to the OneControl bridge, which is running OpenHab (read-only).  This connection sync's the OneControl state with an MQTT instance (I am using the official addon).  Once the connection is made, YAML files are used to create the devices within Home Assistant.
