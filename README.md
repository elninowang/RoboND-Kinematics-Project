[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)
# Robotic arm - Pick & Place project  机器人手臂 - Pick＆Place项目

Make sure you are using robo-nd VM or have Ubuntu+ROS installed locally.

确保您正在使用robo-nd VM或在本地安装Ubuntu + ROS。

### One time Gazebo setup step: 一次Gazebo设置步骤：
Check the version of gazebo installed on your system using a terminal:

使用终端检查系统上安装的Gazebo的版本：

```sh
$ gazebo --version
```
To run projects from this repository you need version 7.7.0+
If your gazebo version is not 7.7.0+, perform the update as follows:

要从此仓库运行项目，您需要版本7.7.0+
如果您的gazebo版本不是7.7.0+，请执行以下更新：

```sh
$ sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
$ wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install gazebo7
```

Once again check if the correct version was installed:

再次检查是否安装了正确的版本：
```sh
$ gazebo --version
```
### For the rest of this setup, catkin_ws is the name of active ROS Workspace, if your workspace name is different, change the commands accordingly

对于其余的设置，catkin_ws是活动的ROS Workspace的名称，如果您的工作区名称不同，请相应更改命令

If you do not have an active ROS workspace, you can create one by:

如果您没有活动的ROS工作区，则可以通过以下方式创建一个：
```sh
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

Now that you have a workspace, clone or download this repo into the **src** directory of your workspace:

现在您有一个工作区，克隆或将这个repo下载到工作区的 **src** 目录中：
```sh
$ cd ~/catkin_ws/src
$ git clone https://github.com/udacity/RoboND-Kinematics-Project.git
```

Now from a terminal window:

现在从终端窗口：

```sh
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y
$ cd ~/catkin_ws/src/RoboND-Kinematics-Project/kuka_arm/scripts
$ sudo chmod +x target_spawn.py
$ sudo chmod +x IK_server.py
$ sudo chmod +x safe_spawner.sh
```

Build the project:
```sh
$ cd ~/catkin_ws
$ catkin_make
```

Add following to your .bashrc file

添加以下.bashrc文件
```
export GAZEBO_MODEL_PATH=~/catkin_ws/src/RoboND-Kinematics-Project/kuka_arm/models

source ~/catkin_ws/devel/setup.bash
```

For demo mode make sure the **demo** flag is set to _"true"_ in `inverse_kinematics.launch` file under /RoboND-Kinematics-Project/kuka_arm/launch

对于演示模式，请确保在 /RoboND-Kinematics-Project/kuka_arm/launch 下的`inverse_kinematics.launch` 文件中将 **demo** 标志设置为 _"true"_

In addition, you can also control the spawn location of the target object in the shelf. To do this, modify the **spawn_location** argument in `target_description.launch` file under /RoboND-Kinematics-Project/kuka_arm/launch. 0-9 are valid values for spawn_location with 0 being random mode.

此外，您还可以控制货架中目标对象的产生位置。 为此，请在 /RoboND-Kinematics-Project/kuka_arm/launch 下的 `target_description.launch` 文件中修改 **spawn_location**参数。 0-9是spawn_location的有效值，0是随机模式。

You can launch the project by

您可以启动项目
```sh
$ cd ~/catkin_ws/src/RoboND-Kinematics-Project/kuka_arm/scripts
$ ./safe_spawner.sh
```

If you are running in demo mode, this is all you need. To run your own Inverse Kinematics code change the **demo** flag described above to _"false"_ and run your code (once the project has successfully loaded) by:

如果您正在演示模式下运行，这是您需要的。 要运行您自己的反向运动代码，将上述 **demo** 标志更改为_"false"_，并运行代码（一旦项目成功加载）：
```sh
$ cd ~/catkin_ws/src/RoboND-Kinematics-Project/kuka_arm/scripts
$ rosrun kuka_arm IK_server.py
```
Once Gazebo and rviz are up and running, make sure you see following in the gazebo world:

一旦Gazebo和rviz开始运行，请确保您在gazebo世界中看到以下内容：

	- Robot 机器人
	
	- Shelf 架
	
	- Blue cylindrical target in one of the shelves 一个架子上的蓝色圆柱形目标
	
	- Dropbox right next to the robot Dropbox就在机器人的旁边
	

If any of these items are missing, report as an issue.

如果任何这些项目丢失，报告为一个问题。

Once all these items are confirmed, open rviz window, hit Next button.

一旦所有这些项目被确认，打开rviz窗口，点击下一步按钮。

To view the complete demo keep hitting Next after previous action is completed successfully.

要查看完成的演示，在上一步操作成功完成后，保持按住“下一步”。

Since debugging is enabled, you should be able to see diagnostic output on various terminals that have popped up.

由于启用了调试功能，因此您可以看到已经弹出的各种终端的诊断输出。

The demo ends when the robot arm reaches at the top of the drop location. 

当机器人臂到达放置位置的顶部时，演示结束。

There is no loopback implemented yet, so you need to close all the terminal windows in order to restart.

没有环回实现，所以你需要关闭所有的终端窗口才能重新启动。

In case the demo fails, close all three terminal windows and rerun the script.

如果演示失败，请关闭所有三个终端窗口并重新运行脚本。

