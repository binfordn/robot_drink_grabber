# robot_drink_grabber

A proof of concept program that demonstrates the use of dynamically generated GUI elements during runtime, as opposed to having a predefined static layout.

The scenario that this program imagines is a robot grabbing a drink out of the refrigerator for the user. Assuming the robot has already opened the door and "seen" what drinks are on the shelf, this program subscribes to a ROS topic that contains a simplified translation of the visual data. It uses the data to generate GUI elements that allow the user to select which drink they want on their computer or mobile device. When the user makes their selection, the program publishes it to another ROS topic.

For now, this program can only process one shelf with one row of drinks. So for example, there might be two drinks on the left, a space with no drink, and then another drink. The simplified visual data would look like this:

00_0  

The program would use this data to generate four buttons:

[0] [1] [_] [3]


The user would also receive an image or stream of the actual visual data, allowing them to make their selection. So if they wanted the drink on the left, they would press the [0] button to tell the robot to grab it. A [_] button represents an empty slot.

Usage:
1. roslaunch rosbridge_server rosbridge_websocket.launch port:=<port_number>
2. Open drink_grabber.html in your browser
3. Publish a std_msgs/String message containing only "0" and "_"
4. Make your drink selection with the buttons!

Uses Robot Web Tools' roslibjs: https://github.com/RobotWebTools/roslibjs/blob/develop/build/roslib.js
