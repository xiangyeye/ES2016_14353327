## 安装ROS 

###ROS操作系统介绍
ROS(Robot Operating System）是一个机器人软件平台，它能为异质计算机集群提供类似操作系统的功能。	ROS的前身是斯坦福人工智能实验室为了支持斯坦福智能机器人STAIR而建立的交换庭(switchyard）项目。

### 安装步骤
我的虚拟机是Ubuntu 16.04 64位的,所以根据这个链接来安装ROS

http://wiki.ros.org/kinetic/Installation/Ubuntu

###1.1 Configure your Ubuntu repositories

###1.2 Setup your sources.list（添加sources.list）

	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

###1.3 Set up your keys（添加keys）

	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

###1.4 Installation

先update一下，确保自己的软件包是最新的

	sudo apt-get update

Desktop-Full Install (桌面完整安装)：

	sudo apt-get install ros-kinetic-desktop-full


###1.5 Initialize rosdep（初始化rosdep）

	sudo rosdep init
	rosdep update


###1.6 Environment setup(环境配置)
	echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
	source ~/.bashrc
###1.7 Getting rosinstall
	sudo apt-get install python-rosinstall



## 测试ROS是否安装成功
 打开第一个终端，输入指令：
	roscore
	
<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS1.png" width = "500" alt="configure" />


 打开第二个终端，开启小乌龟界面，输入指令：
	rosrun turtlesim turtlesim_node
得到小乌龟界面：

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS2.png" width = "500" alt="configure" />

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS3.png" width = "500" alt="configure" />


打开第三个终端，输入指令，按键盘上的箭头，移动小乌龟：

	rosrun turtlesim turtlesim_teleop_key
<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS4.png" width = "500" alt="configure" />
按上键，看到小乌龟移动，图片中有移动的轨迹

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS5.png" width = "500" alt="configure" />


	
打开第四个终端，输入指令，看到ROS nodes以及Topic等图形展示：

	rosrun rqt_graph  rqt_graph
<img src="https://raw.githubusercontent.com/xiangyeye/image/master/ROS6.png" width = "500" alt="configure" />

通过这些指令测试，表明我们的ROS安装成功了。

### 实验感想

本次实验很简单，照着官网上的步骤，把指令跑一遍就好了，只是中间install的步骤等到很久之外，其他都没什么问题。只是我一开始不知道怎么测试我的ROS有没有安装成功，后来问了别人，发现测试一次性通过。
