## Project: Kinematics Pick & Place 项目：运动学 拿起&放下
### Writeup Template: You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.、

编写模板：如果您要将其作为一个标记文件提交，您可以使用此文件作为模板，但如果愿意，请随时使用其他方法并提交pdf。

---


**Steps to complete the project: 完成项目的步骤：**  


1. Set up your ROS Workspace.
2. Download or clone the [project repository](https://github.com/udacity/RoboND-Kinematics-Project) into the ***src*** directory of your ROS Workspace.  
3. Experiment with the forward_kinematics environment and get familiar with the robot.
4. Launch in [demo mode](https://classroom.udacity.com/nanodegrees/nd209/parts/7b2fd2d7-e181-401e-977a-6158c77bf816/modules/8855de3f-2897-46c3-a805-628b5ecf045b/lessons/91d017b1-4493-4522-ad52-04a74a01094c/concepts/ae64bb91-e8c4-44c9-adbe-798e8f688193).
5. Perform Kinematic Analysis for the robot following the [project rubric](https://review.udacity.com/#!/rubrics/972/view).
6. Fill in the `IK_server.py` with your Inverse Kinematics code. 

1. 设置您的ROS工作区。
2. 将[project repository](https://github.com/udacity/RoboND-Kinematics-Project) 下载或克隆到您的ROS Workspace的 ***src*** 目录中。
3. 尝试前进动力学环境，熟悉机器人。
4. 在[demo mode](https://classroom.udacity.com/nanodegrees/nd209/parts/7b2fd2d7-e181-401e-977a-6158c77bf816/modules/8855de3f-2897-46c3-a805-628b5ecf045b/lessons/91d017b1-4493-4522-ad52-04a74a01094c/concepts/ae64bb91-e8c4-44c9-adbe-798e8f688193)中启动。
5. 按照  [project rubric](https://review.udacity.com/#!/rubrics/972/view) 对机器人进行运动分析。
6.用“反向运动学”代码填写“IK_server.py”。


[//]: # (Image References)

[image1]: ./misc_images/misc1.png
[image2]: ./misc_images/misc3.png
[image3]: ./misc_images/misc2.png

## [Rubric](https://review.udacity.com/#!/rubrics/972/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

在这里，我将分别考虑这些标题，并描述我在实现过程中对每一个问题的解决方法。

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

提供一个写入/自述文件，其中包含所有的标题以及如何处理每个要点。 您可以提交您的写作作为降价或pdf。

You're reading it! 你正在读它！

### Kinematic Analysis 运动学分析
#### 1. Run the forward_kinematics demo and evaluate the kr210.urdf.xacro file to perform kinematic analysis of Kuka KR210 robot and derive its DH parameters.  

1. 运行forward_kinematics演示，并评估kr210.urdf.xacro文件，以执行Kuka KR210机器人的运动学分析，并得出其DH参数。

Here is an example of how to include an image in your writeup.

这是一个如何在你的写作中包含一个图像的例子。

![alt text][image1]

#### 2. Using the DH parameter table you derived earlier, create individual transformation matrices about each joint. In addition, also generate a generalized homogeneous transform between base_link and gripper_link using only end-effector(gripper) pose.

2. 使用先前导出的DH参数表，创建关于每个关节的单个变换矩阵。 此外，还使用仅使用末端执行器（抓爪）姿势的base_link和gripper_link之间生成广义均匀变换。

Links | alpha(i-1) | a(i-1) | d(i-1) | theta(i)
--- | --- | --- | --- | ---
0->1 | 0 | 0 | L1 | qi
1->2 | - pi/2 | L2 | 0 | -pi/2 + q2
2->3 | 0 | 0 | 0 | 0
3->4 |  0 | 0 | 0 | 0
4->5 | 0 | 0 | 0 | 0
5->6 | 0 | 0 | 0 | 0
6->EE | 0 | 0 | 0 | 0


#### 3. Decouple Inverse Kinematics problem into Inverse Position Kinematics and inverse Orientation Kinematics; doing so derive the equations to calculate all individual joint angles.

3. 将反向运动学问题分解为反向位置运动学和逆向运动学; 这样做导出方程来计算所有单个关节角度。

And here's where you can draw out and show your math for the derivation of your theta angles. 

在这里，您可以绘制出您的数学角度来推导您的角度。

![alt text][image2]

### Project Implementation 项目实施

#### 1. Fill in the `IK_server.py` file with properly commented python code for calculating Inverse Kinematics based on previously performed Kinematic Analysis. Your code must guide the robot to successfully complete 8/10 pick and place cycles. Briefly discuss the code you implemented and your results. 

1.使用正确注释的python代码填写“IK_server.py”文件，用于根据先前执行的运动学分析计算反运动学。 您的代码必须指导机器人成功完成8/10个拾取和放置循环。 简要讨论您实现的代码和结果。

Here I'll talk about the code, what techniques I used, what worked and why, where the implementation might fail and how I might improve it if I were going to pursue this project further.  

在这里，我将讨论代码，我使用了什么技术，什么工作以及为什么，实施可能会失败，以及如果我将进一步追求这个项目，我可以如何改进它。

And just for fun, another example image:

只是为了好玩，另一个例子形象：

![alt text][image3]


