# ROS_installation_guide
This is an instruction of installing Robotic Operating System (Melodic) on Ubuntu 18.4 with additional installing of robotic arm
**The following steps for windows users if you already installed VirtualBox or running Ubnutu please refer to step: 4**
1. Download [VirtualBox](https://www.virtualbox.org/wiki/Downloads) by clicking on windows hosts
2. Download [Ubnutu](https://releases.ubuntu.com/18.04/) desktop image preferably version 18.4 
3. Configure VirtualBox with the minimum requirements of 4GB's of RAM and 2 core's of CPU.
4. Install ROS Melodic repo by opening the terminal and typing: `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu bionic main" > /etc/apt/sources.list.d/ros-melodic.list'`
5. Next we will add official ROS key to authenticate the package: `sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654`
   - If you are prompt with the error "`Could not get lock /var/lib/dpkg/lock`" remove the lock by typing: `sudo rm lock /var/lib/dpkg/lock` and that should hopefully resolve the issue.
6. Update the package to make sure it is up to date by using `sudo apt update`
7. Install ROS recommended desktop version `sudo apt install ros-melodic-desktop-full`
8. Set up ROS Melodic environment `echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc`
   - `source ~/.bashrc`
10. You can verify the installation by using `roscore`
11. Install dependencies for building packages `sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential` 
12. And finally before using any ROS tools you will need to initalize rosdep `sudo apt install python-rosdep` 
    - Initalize it with `sudo rosdep init`
    - `rosdep update`
 Knowing issue ***Unable to locate package ros-melodic-desktop-full*** the way to fix it is by properly following step 4,5,6 and making sure they are installed as well as running `run sudo apt update`
 
**Down below are the steps for installing arduino robotic arm from Smart method repository**
Create a workspace for catkin_make by running the following commands:
1. Install prerequisites `source /opt/ros/noetic/setup.bash`
2. Create and build a catkin workspace:
   - `mkdir -p ~/catkin_ws/src`
   - `cd ~/catkin_ws/`
   - `catkin_make`
3. Source your new setup. sh file: `source devel/setup.bash`
   - source ~/.bashrc
4. Add the “arduino_robot_arm” package to “src” folder: 
   - cd ~/catkin_ws/src
   - sudo apt install git
   - git clone https://github.com/smart-methods/arduino_robot_arm 
   
5. Install all the dependencies: 
   - cd ~/catkin_ws
   - rosdep install --from-paths src --ignore-src -r -y
   - sudo apt-get install ros-melodic-moveit
   - sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
   - sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
   - sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

6. Compile the package by running `catkin_make`
7. Launch the package by typing `roslaunch robot_arm_pkg check_motors.launch`
And you should have something like this: 
![ros_robot_arm](https://user-images.githubusercontent.com/53359513/122626716-a2442e00-d0b4-11eb-9324-7c81219c9ab9.jpg)
![ros_robot_arm2](https://user-images.githubusercontent.com/53359513/122626807-023ad480-d0b5-11eb-970b-f58c6bc9adab.jpg)
![ros_robot_arm3](https://user-images.githubusercontent.com/53359513/122626808-04049800-d0b5-11eb-8bf6-76887030855e.jpg)

