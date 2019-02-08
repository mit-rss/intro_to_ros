# Intro to ROS
The objective of the following exercises is to help you practice the most commonly used concepts in ROS. We provide a quick reference document and pointers to relevant documentations. Feel free to use all the resources available to you to learn the concepts as thoroughly as possible and complete the exercises as efficiently as possible. All your work in this section should be done on the repository directory from the previous section and should be pushed after the completion of each exercise.

Although you're encouraged to collaborate with others if you are stuck, the lab should be completed individually so you can get practice with skills that will be essential later on in the course when you are in teams. If you have general questions, please post on [Piazza](https://piazza.com/class/jrql7urlkqn189) so other students can benefit from the answer. If you have a question about your individual submission, please make a private post. 

### Submission
Each exercise has defined submission requirements and the overall assignment submission requirement follows from that. However, for your work to be graded make sure that the following two requirements are met by all your submissions.
1. Everything submitted in this section should be in your git repository created earlier (the beginning of the Git exercises) and must be committed from the terminal.
2. All your work should live in your workspace and more specifically your package. Make sure that your workspace builds before each submission.
3. Finally, when you have all your nodes running smoothly, submit a `.zip` file of your package (**ros_exercises**) to [Gradescope](https://gradescope.com/) under lab1b_exercises_ros. The zip should be just your package with all your work tested and ready to go. Note: Make sure that node specifications match the requirements. Your submission will not get graded properly if you don't put it in the right format.   

This lab is due on **TBD**.

### References
The following are selected chapters from the ROS Wiki documentations and Tutorials. If you understand all the concepts covered in these exercises, you should be ready for the following exercises and for the most of the ROS related tasks you will be performing throughout the first few labs. For more on ROS, visit the [ROS Wiki Documentation](http://wiki.ros.org/) section and follow the links to learn more.
1. [Catkin](http://wiki.ros.org/catkin/conceptual_overview)
2. Catkin Workspace
	a. [Catkin workspaces](http://wiki.ros.org/catkin/workspaces)
	b. [Creating Catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace)
3. Packages
	a. [ROS package](http://wiki.ros.org/Packages)
	b. [Creating ROS package](http://wiki.ros.org/catkin/Tutorials/CreatingPackage)
4. Messages
	a. [ROS Messages](http://wiki.ros.org/Messages)
	b. [Creating custom messages](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv)
	c. [The rosmsg command-line tools](http://wiki.ros.org/rosmsg)
	d. [Common ros message categories](http://wiki.ros.org/common_msgs)
5. Topics 
	a. [ROS Topics](http://wiki.ros.org/Topics)
	b. [Rostopic Command-Line tool](http://wiki.ros.org/rostopic)
6. Nodes
	a. [ROS Nodes](http://wiki.ros.org/Nodes)
	b. [The rosnode command-line tools](http://wiki.ros.org/rosnode)
	c. [Writing Publisher and Subscriber(Python)](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29)
7. Launch Files 
	a. [ROS Launch](http://wiki.ros.org/roslaunch)
	b. [Command-line Tools](http://wiki.ros.org/roslaunch/Commandline%20Tools)
	c. [XML Format](http://wiki.ros.org/roslaunch/XML)
	d. [Tips for Large Projects](http://wiki.ros.org/roslaunch/Tutorials/Roslaunch%20tips%20for%20larger%20projects)
8. Parameter server
	a. [Parameter server](http://wiki.ros.org/Parameter%20Server)
	b. [rosparam](http://wiki.ros.org/rosparam)
9. Visualization Tools
	a. RQT
		i. [RQT](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics)
		ii. [RQT_GRAPH](http://wiki.ros.org/rqt_graph)
	b. RVIZ
		i. [User Guide](http://wiki.ros.org/rviz/UserGuide)
		ii. [Interactive Markers](http://wiki.ros.org/rviz/Tutorials/Interactive%20Markers%3A%20Getting%20Started)
		iii. [Tutorials](http://wiki.ros.org/rviz/Tutorials)
10. TF
	a. [Tf](http://wiki.ros.org/tf)
11. Rosbag
	a. [Rosbag](http://wiki.ros.org/Bags) 
	b. [Command-Line Tools](http://wiki.ros.org/rosbag/Commandline)


### ROS Exercises
### Question 1: Create a package and build it
By following the instructions from the reference or instructions of your finding, create a catkin workspace and package named rss_lab1 and ros_exercises respectively, and make sure that your workspace is built (using [catkin_make](http://wiki.ros.org/catkin/commands/catkin_make)) before and after the package was added. Your workspace should live in the repository created in the Git exercises. After creating the workspace and the package, you should have the following directory layout.

* /rss_lab1[your git repository created in lab1b]
    * /rss_lab1[your catkin workspace]
	    * /src
	    	* /ros_exercises[Your catkin package]
	  	* /devel[automatically generated by catkin_make]
	  	* /build[automatically generated by catkin_make]
	  	* [other ros related files and packages if any]
    * [files and directories from lab1a_linux and lab1b_git]

**Note**: Push your workspace.

### Question 2: Create Simple Publisher (Python)
 
