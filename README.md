# self-driving-car

[TOC]

- core components of self-driving cars
- How baidu Apollo open source self-driving car software  implements these core components.
- How self-driving car work from one end to the other.


## Main part
Target: Understand how self-driving car work.

Main sections of the Apollo open-source self-driving car platform.

- high-definition maps(central module of self-driving car)
    underpin almost every other part of the software stack, include localization, perception, prediction and planning.

- localization
    How the car determines its location in the word.
- perception
    How self-driving car sees the world.Deep learning is an important and powerful tool for perception.  Convolutional neural networks which make up a branch of deep learning. are critical to perception tasks, such as classification, detection and segmentation.These approaches word with data from several different self-driving car sensors, including cameras, radar and lidar.
- prediction
    Different way to predict how other vehicle or pedestrains might move. How to combine predictin and routing to generate a trajectory for vehicle.
- planning
    Planning is one of the hardest parts of building a self-driving car.
- control
    Hot to use steering, throttle and break to execute planned trajectory. Several different types of controllers which range from simple to increasingly complex but also increasingly powerful.



## The history of the transportation

  One million yeas ago, our human ancestors begin to walk and run on two feet. This liberated out hands so that eventually, we could do things like walk and text at the same time.

  About 4,000 years ago, humans began building horse-drawn carriages. Carriages are actually one of the earliest examples of humans building vehicle.

  One hundred years ago, humans invented modern automobiles. Cars make it possible to go further and faster then ever before.

  Now we are at the cusp of a new era of self-driving cars. We hope that self-driving cars make the world safer and more productive, and better than ever before.

> Why do we need self-driving cars?

  The most important reason is safety. Human drives wind up in a lot of automobile collisions. Over one million people around the world die in automobiles crashes every single year; Self-driving cars have a lot of advantages over humans drivers. In particular, self-driving cars don't get drunk, and they don't get tired, and they don't get distracted.

  Self-driving cars also learn form each other. As humans, every one of us has to learn to drive from scratch, and we make almost of the same mistakes that our parents and grandparents made when they were learning to drive. Self-driving cars, on the other hand, learn to drive from each other self-driving car that has ever been on the road. So they immediately start out as experienced drivers.

  Self-driving cars also benefits beyond safety. Think about the last time you went to the grocery store, maybe over the weekend, and had to drive around and around looking for a parking spot. Now imagine a future world in which parking doesn't exist because a self-driving vehicle drops you off right where you need to be, just like a taxi or a ride-sharing vehicle. Think about how much more pleasant and a less stressful that world be.

Compare

Humans driving.
- High Traffic Accident Rate
- Learn to drive from scratch
- Parking Trouble

Self-driving cars.
- More Reliable Driving
- Learnable Driving System
- No Parking Trouble


  The Society of Automotive Engineers identifies six levels of autonomous vehicles, zero through five.
![Levels of Driving Automation](./images/levels-of-driving-automation.png)

- Level zero is the base level. At this level, the drives is the sole decision-marker for the system. The driver controls the steering wheel, throttle, breaks and all other vehicle controls.
- Level one is Drive Assistance. At this level, the vehicle support the driver with ether steering or acceleration. Cruise control, for example, is a level one automation system. At this level, drivers must stay fully engaged, but they can give up some control to the autonomous system.
- Level two is partial automation. At this stage, the vehicle controls several functions automatically such as automatic cruise control and lane keeping. However, the driver must still perform any functions that the autonomous system does not handle.
- Level three is conditional automation. The vehicle drives autonomously, but the driver must be ready to tike over whenever necessary.
- Level four is high automation. At this level, the vehicle controls all aspects of the driving experience and there is no expectation that the human driver will ever intervene. In fact, at this level, ti's possible that the vehicle might not even have a steering wheel or driver controls at all. However, at this level, the vehicle may be restricted to certain areas. Often, this is called a geofence. The vehicle can operate completely autonomously within a certain geofence, but outside of that geofence, the vehicle is either unable to operate autonomously or maybe unable to operate at all.
- Level five, the highest level, is full automation. At this level, the vehicle operates completely autonomously anywhere and everywhere that a human can drive. Level five should be automation as good or better than a human driver in all scenarios.  


## Self-driving car history

![Self-driving car history](./images/self-driving-car-history.png)

  Research into self-driving cars began in the 1980s. In 1986, Carnegie Mellon University's NavLab built one of the first self-driving cars that was ever controlled by a computer.
  In 1995, Mercedes Benz completed the Eureka Prometheus Project, which was the largest autonomous vehicle research and development program in history up to that time. This project redefined the state of the art for self-driving vehicles. Many universities and car manufacturers participated in this pan-European project from 1987-1995.
  In 2005, Sebastian Thrun, who was also the founder of Udacity, Led the Stanford racing team that won the DARPA Grand Challenge, a 100 mile self-driving car race through the California desert. Aster winning the DARPA Grand Challenge, Sebastian joined Google and started the Google self-driving car project in 2009. Over the last few years, self-driving car tests have launched in San Fransisco, and Phoenix, and Las Vegas, and Detroit, and Boston, and Beijing, and many other cities all around the world.
  In 2017, Baidu released an open-source self-driving car project called Apollo. This platform helps partners integrate their own vehicles and hardware systems to build complete autonomous systems. An autonomous vehicle is comprised of special purpose computers and sensors. autonomous computing units are 10 times faster the personal computers or more.
  In the Apollo system, the vehicles's onboard computing units are supported by a massively powerful cloud cluster. Any given autonomous vehicles has many advanced sensors that perform tasks like perception and localization. With artificial intelligence and these sensors, the vehicles can operate itself independently of any human driver.

## How the self-driving car work

![5 core components](./images/5-core-components-of-self-driving-car.png)

  Self-driving car have 5 core components.
  - Computer vision
  - Sensor Fusion
  - Localization
  - Path planning
  - Control
Computer vision is how we use camera images to figure out what the word arounds us looked like and sensor fusion is how we incorporate data from other sensors like lasers and radar to get a richer understanding of our environment. Once we built this deep understanding of what the word around us is, we use localization to figure out precisely where we are in that word and then once we figured out where we are in the world and what the world looks like, we use path planning to chart a course through the world to get us where we'd like to go and then the final step is control, which is how we actually turn the steering wheel and hit the throttle and hint the break in order execute the  trajectory that we built during the path planning.

But Apollo platform structure is a little different from this. Apollo is use high-definition maps and localization module as the core, and other all based on these tow.

![apollo-platform-structure](./images/apollo-platform-structure.png)

Apollo open-source platform provides hardware specifications on vehicle software, and cloud services,  high-definition map services and then open autonomous driving simulation engine. Apollo technology framework consists of four layers, reference vehicle platform, reference hardware platform, open software platform, and cloud services platform. we will learn how they integrate to create an end-to-end self-driving car.

> reference vehicle platform

It's also called drive-by-wire vehicle

> reference hardware platform.

The car have several sensors which are defined by the hardware reference specification. The Controller Area Network or CAN, is the vehicle's internal communication network.
![CAN Card](./images/CAN-card.png)

The CAN card, is how your computer system connects to the car internal network, to send signals for acceleration, braking and steering.
![GPS receiver](./images/GPS-receiver.png)
The Global Position System or GPS receives signals from satellites, circling the earth. The signals help us to determine our location.
![internal-measurement-unit](./images/internal-measurement-unit.png)
 The internal measurement unit or IMU, measures the vehicle movement and location, by tracking the position, speed, acceleration and other factors.
![LiDAR](./images/LiDAR.png)
LiDAR is an array of pulse lasers, the LiDAR that Apollo uses can scan 360 degrees around the vehicle.
![laser beams](images/laser-beams.png)
The reflection of this laser beams, builds the points cloud that our software that our software can use understand the environment.
![cameras](./images/LiDAR.png)
Camera capture the images data. We can use computer vision to extract the contents of these images and understand the environment around us. For example, because the cameras can perceive color, we use theme to detect and understand the traffic light.
![radar](./images/radar.png)
Radar is also used for detecting obstacles. Radar has low resolution, which makes it difficult to understand what kind of obstacle that radar have detected. But the advantage of radar are that it is economical and it works in all weather, and lighting condition. Radar is also particularly very good at measuring the speed of other vehicles.
![Major hardware components of self-driving car](./images/sensors-of-self-driving-car.png)
Here is an example of how the major hardware components including camera, radar, LiDAR, GPS-IMU and IPC could be installed on a vehicle. This hardware is what you need to run Apollo.


> open software platform

Overall framework: The open software layer is divided into three sub layers:
- real-time operating system(ROTS)
- Runtime framework
- A layer of application modules.

The real-time operating system guarantees that certain task will be completed within a given time.  Real-time refers to the fact that operating system of self-driving car can produce timely calculations, analysis and execute corresponding actions in a short time, aster the car sensors collect the data form the outside world. For example, imagine a self-driving car sensor detect a moving obstacle in front of the vehicle. In a short time, the Apollo software modules based on RTOS must analyze whether the obstacle is a pedestrain, or a car, or something else. Predict it's future movement direction and speed, and determine where to slow down or to stop. Then the vehicle must execute the decision. Real-time performance is an important requirement for ensuring system stability and driving safety. Apollo RTOS is combination of Ubuntu Linux operating system and the Apollo kernel. The original Ubuntu system is not a real-time operating system. By adding in an Apollo-designed kernel, we can make it RTOS.

The Runtime Framework is the operating environment of Apollo, which is a customized version ROS. The Robot Operating System. ROS has a long history in the robotics industry and there are currently more than 3,000 basic libraries that support the rapid development of applications. ROS divides the autonomous system into multiple modules based on the functions. Each modules is responsible for receiving, processing and publishing it's own messages. Because the modules are independent and communicate only through the Runtime Framework, adjusting any single module is easy. ROS is the most widely used robotic framework and thus contains modules for many of the most recent breakthroughs. All of those features make ROS the ideal development and the integration framework for Apollo. In order to adapt ROS for self-driving cars. the Apollo team has improved functionality and performance for shared memory, decentralization and data comparability. Shared memory reduces the need to copy data if different modules require to access. For a one-to-many transmisson scenario share memory supports the "write once, read multiple" pattern. This can accelerate communication. Decentralization solves the problem of a single point of failure. Off-the-shelf ROS is composed of many nodes. Each nodes has its own corresponding function. For example, one node may be responsible for collecting camera images, the different node may be responsible for planning a trajectory, and yet anther node might be responsible for sending to he vehicle commands to the vehicle on the canbus. But all these nodes need to be controlled by a single ROS master node. If this master node fails, the entire system will fail. To avoid this problem, Apollo brings all the nodes together into a common domain. Each node in the domain has the information about the other nodes in the domain. Through this decentralization scheme, the common domain has replaced the original ROS Master node. Thus, the risk the single points of failure has been eliminated. For self-driving, due to the large size of the project itself. Data compatibility is crucial. Different ROS nodes communicate with each other through an interface language called ROS Message. ROS message requires a common interface language so that each node can interpret the message data form the other nodes. If the format in the message file is even slightly different from what a node is expecting, the communication will simply fail. This can leads to serious comparability issues. For example, when an interface is upgraded, data incompatibility will ofter result in system failure. Also, previous recorded test data must be converted again and again to adopt to new message formats. To solve this problem, the Apollo team use another interface language called Protobuf instead of native ROS message. Protobuf is a method of serializing structured data. It is used in developing programs to communicate with each other over a wire or for string data. You can add new fields to your message formats without breaking backwards-compatibility. New binaries can accept the old message format during parsing. Adding the Protobuf format to ROS helps the long term development of Apollo.

Application modules. Apollo software platform has a variety of modules, these modules include MAP engine, localization, perception, planning, control, end-to-end driving and the human-machine interface or HMI. Each module has its own algorithm library, and the relationships between the modules are complex. We will study this module and how they are related to each other throughout this course.

> cloud services platform
