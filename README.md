
| **Due Date**  | **Monday, February 14th at 1:00PM EST**                                 |
|---------------|----------------------------------------------------------------------------|
|  **Submission**   | `log.npf` and `ros_exercises.zip` on [Gradescope](https://gradescope.com/) (listed as two separate assignments)|

# Lab 1C: Intro to ROS

## Introduction
The objective of the following exercises is to help you practice the most commonly used concepts in ROS. We provide a quick reference document and pointers to relevant documentations. Feel free to use all the resources available to you to learn the concepts as thoroughly as possible and complete the exercises as efficiently as possible.

Although you're encouraged to collaborate with others if you are stuck, the lab should be completed individually so you can get practice with skills that will be essential later on in the course when you are in teams. If you have general questions, please post on [Piazza](https://tinyurl.com/RSS2021-piazza) so other students can benefit from the answer. If you have a question about your individual submission, please make a private post.

## Submission
You are meant to complete this lab by testing your code and verifying the results on your own, as you would do in real life. Once you are confident in your answers, your lab will be graded against our automated tests. Please refer to the next section, **Automated Tests** for instructions on how to run these tests. You will be submitting the resulting `log.npf` file to "Lab 1C: Intro to ROS -- log.npf submission" on Gradescope, in addition to a zip file containing your local repository (`ros_exercises.zip`) to "Lab 1C: Intro to ROS -- Git repo submission".

The due date is listed at the top of this document.

### Automated Tests

You can download the test binary to check your solutions locally by going to the [releases page of this repo](https://github.com/mit-rss/intro_to_ros/releases) and downloading the ```run_tests``` binary. **Make sure you place the binary in your ```ros_exercises``` folder.**:

    mv run_tests ~/catkin_ws/src/ros_exercises/

Then make the binary executable with ```chmod```

    chmod +x run_tests

First, kill all running ROS processes. Then start ```roscore```.

Finally, run the following in a new terminal to begin testing:

     cd ~/catkin_ws/src/ros_exercises/
    ./run_tests

You should be graded on the completion of 6 tests. Be careful with naming the various files defined in the handout correctly or else you won't be graded properly. Also, **be sure to `cd` into `ros_exercises` before running the tests**, or the automated tests may use the wrong paths to each of the files it checks for.

Additionally the `run_tests` file will generate a file called `log.npf` which you **must upload to gradescope for credit**.


### Automatic grade Breakdown

This table shows how the different tasks will be graded by the automated grader.
| Task                    |      Grade        |
|-------------------------|-------------------|
| Simple Publisher        |      0.5 points   |
| Simple Subscriber       |      0.5 Points   |
| Complex Publisher       |      0.5 Points   |
| Complex Subscriber      |      1.0 Points   |
| Launch File             |      0.5 Points   |
| **Total**               |   **3.0 Points**  |



### Manual Grading Portion
If you have successfully completed all parts, you should receive a score of 3.0/4.0 on Gradescope. The rest of your score (1.0 points) will be a manual grading of your package ``ros_exercises`` by the staff of your git repository, which should be avaliable on your `github.mit.edu` account. Submit a zip file of your repository to the Gradescope assignment **Lab 1C: Intro to ROS -- Git repo submission**

### The Manual Grade Breakdown
This table shows the grading breakdown of the manually graded portion of the lab.
| Task                                | Grade          |
|-------------------------------------|----------------|
| Simple Publisher RQT Screenshot     | 0.1 Points     |
| Simple Subscriber RQT screenshot    | 0.1 Points     |
| Fake Scan RViz ScreenShot           | 0.1 Points     |
| Open Space Publisher RQT Screenshot | 0.2 Points     |
| Custom Message file inspection      | 0.2 Points     |
| Launch file inspection              | 0.1 Points     |
| Setting  ROS parameters	      | 0.2 Points     |
| **Total**                           | **1.0 Points** |

## Setup
Before you get started with this lab, make sure you have the proper dependencies installed by following Steps 1.5 to 1.7 in [this guide](https://wiki.ros.org/melodic/Installation/Debian).

### References

The following are selected chapters from the ROS Wiki [Documentation](http://wiki.ros.org/) and [Tutorials](http://wiki.ros.org/ROS/Tutorials). If you understand all the concepts covered in these exercises, you will be ready for the exercises of this lab (given below) and for most of the ROS related tasks you will be performing throughout the first few labs. For more on ROS, visit the [ROS Wiki](http://wiki.ros.org/) section and follow the links to learn more.

Additionally, useful ROS cheatcheets can be found [here](https://kapeli.com/cheat_sheets/ROS.docset/Contents/Resources/Documents/index) and [here](https://www.datamachinist.com/wp-content/uploads/2020/05/ROS_cheat_sheet.pdf).

**Note:** We are using ROS Melodic and catkin for this class. Some links may have instructions for different ROS distribuitions / or build systems; make sure to select the correct one.

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
	a. rqt   
		- [rqt](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics)   
		- [rqt_graph](http://wiki.ros.org/rqt_graph)   
	b. RViz   
		- [User Guide](http://wiki.ros.org/rviz/UserGuide)   
		- [Interactive Markers](http://wiki.ros.org/rviz/Tutorials/Interactive%20Markers%3A%20Getting%20Started)   
		- [Tutorials](http://wiki.ros.org/rviz/Tutorials)   
10. [TF](http://wiki.ros.org/tf)   
11. Rosbag   
	a. [Rosbag](http://wiki.ros.org/Bags)    
	b. [Command-Line Tools](http://wiki.ros.org/rosbag/Commandline)   

**Note:** Some useful **debugging hints** are provided at the end of this document.

## ROS Exercises

### Create a package and build it
By following the instructions from the reference or instructions of your finding, create a catkin workspace named `catkin_ws/`. Inside that workspace, create a new package, named `ros_exercises/`, which should depend on `rospy`, `std_msgs`, and `sensor_msgs`. **Make sure that your workspace is built (using [catkin_make](http://wiki.ros.org/catkin/commands/catkin_make)) before and after the package was added, and do not forget to source `devel/setup.bash`**. Your package (`ros_exercises`) should live in the `/src/` directory, where you add other packages (such as other labs later on). Make your `ros_exercises` a git repo. After creating the workspace and the package, you should have the following directory layout.

* /catkin_ws[your catkin workspace]
	* /src
		* /ros_exercises[Your catkin package]
		* [other ros related files and packages if any]
	* /devel[automatically generated by catkin_make]
	* /build[automatically generated by catkin_make]

**Note**: Push your `ros_exercises/` package.

Additionally, everytime you make an edit to your files, make sure to run `catkin_make` and **source your `setup.bash` file** (_forgetting to source this file can cause some confusing situations, so make sure to always perform this step after `catkin_make`!)_. You will also need to source your setup.bash file each time you open a new terminal window.

## Question 1: Create Simple Publisher (Python)
Your task in this exercise is to create a simple ROS node that publishes a random number between 0 and 10.0. Before you start the following exercise, please make sure that your package is built properly. Note that this file will reside inside of the /ros_exercises folder of your newly created package.

### Node Specification    
**Description:** Publishes a random number between 0 and 10.    
**File name:** simple_publisher.py    
**Node Name:** simple_publisher    
**Published topic names:** my_random_float    
**Message type:** Float32    
**Subscription topic names:** None    
**Publish rate:** 20hz    
### Commit Specification    
1. When your node works properly, take a screenshot of ***rqt_graph*** visualization of your node(s) and topic(s). Name your screenshot `simple_publisher_rqt.png` and save it in `ros_exercises/rqt` (create the `rqt/` directory). Note: `ros_exercises/` is the ros package you created at the beginning of this section.
2. Push your code, the screenshot, and any supporting files with an appropriate commit message.

## Question 2: Create Simple Subscriber (Python)
In this exercise, you will write a listener (subscriber) that listens to the topic ***my_random_float***, which is published to by the previous node. The new node takes the natural log of the message on ***my_random_float*** and publishes it to ***random_float_log***.  

### Node Specification

**Description:** Subscribes to the topic published on by the simple_publisher and publishes the natural log of the received messages.     
**File name:** simple_subscriber.py             
**Node Name:** simple_subscriber       
**Published topic names:** random_float_log    
**Message type:** Float32    
**Subscription topic names:** my_random_float   

### Commit Specification

1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, name it `simple_subscriber_rqt.png`, and save it in the same folder as the previous exercise.
2. Again, push your code, the screenshot, and any supporting files with an appropriate commit message.

## Question 3: Create more Complex Publisher (Python)

In this exercise, you will write a node that publishes fake laser scan data as specified below.   
### Node Specification    
**Description:** Publish a [LaserScan](http://docs.ros.org/api/sensor_msgs/html/msg/LaserScan.html) message with random ranges between 1 and 10.     
**File name:** fake_scan_publisher.py             
**Node Name:** fake_scan_publisher       
**Published topic names:** fake_scan    
**Message type:** LaserScan    
**Subscription topic names:** None     
**Publish Rate:** 20hz   

### LaserScan Parameter Specifications

**Header:**       
	- **Timestamp:** Current ros time     
	- **Frame_id:** “base_link”     
**Angle_min:** (-2/3)*pi*     
**Angle_max:** (2/3)*pi*     
**Angle_increment:** (1/300)*pi*     
**Time_increment:** Leave it unset if you wish     
**Scan_time:** The time difference in seconds between consecutive scans.

**Range_min:** 1.0        
**Range_max:** 10.0       
**Ranges:** One dimensional array with elements of random floats between range_min and range_max, Use angle_min, angle_max,  and angle_increment to determine the length. Be careful of an off by 1 error! There should be an element **at** ```angle_min``` and ```angle_max```.
**Intensities:** Leave it unset if you wish      

### Commit Specification   

1. When your node works properly, visualize the published laser scan data using RViz. Take a screenshot of your visualized laser scan data and name it `fake_scan_rviz.png`. Save the image in `ros_exercises/rviz`
2. Record a bag file of your laser scan data and call the file `fake_scan_bag.bag`, save it in `ros_exercises/rosbag`.
3. Again, push your code, bag file, screenshot, and any supporting files with a appropriate commit message.

Note: You should get an error in RViz that says "No tf data. Actual error: Fixed Frame [map] does not exist". This will not affect your visualization of the laser scan; however, if you would like, you can run `rosrun tf static_transform_publisher 0 0 0 0 0 0 1 map base_link 10` in a separate terminal window to link `map` to your TF tree.

**If you are failing this test make sure you have these files in your ```ros_exercises``` directory**:

- ```rviz/fake_scan_rviz.png```
- ```rosbag/fake_scan_bag.bag```

## Question 4: Create a more complex Subscriber(Python)
Create a node that subscribes to the fake laser scan data and outputs the longest range from the laser scan ranges and its corresponding angle.    
### Node Specification    
**Description:** Subscribes to the fake_scan topic published on by the fake_scan_publisher from the previous exercises, and finds the longest return (the range element with the greatest value) and publishes the corresponding angle and return value or distance.    
**File name:** open_space_publisher.py    
**Node Name:** open_space_publisher    
**Published topic names:** open_space/distance and open_space/angle    
**Message type:** Float32    
**Subscription topic names:** fake_scan    
**Publish rate:** 20hz    
### Commit Specification    
1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, named it `open_space_rqt.png`, and save it in `ros_exercises/rqt`.
2. Again, push your code, the screenshot, and any supporting files with a appropriate commit message.

**If you are failing this test make sure you have these files in your ```ros_exercises``` directory**:

- ```rqt/open_space_rqt.png```

## Question 5: Create a custom Message and Publish it
The publisher from the previous exercise was publishing two related pieces of data on two separate topics (***open_space/angle*** and ***open_space/distance***). In this exercise, we ask you to create a custom message that encapsulates the two pieces of data, the same way the LaserScan message type combines multiple pieces of data, and name your custom message file `OpenSpace.msg`. After creating and compiling your custom message, modify the publisher from the previous exercise to publish this message type on the topic ***open_space***. Hint: Don't forget to modify your `CMakeLists.txt` and `package.xml` files.

**Important:** For grading purposes, it is required that your ***angle*** field be specified **BEFORE** your ***distance*** field. When creating your messages, you will be completely in charge of what your message specification looks like, so be aware that this is just a somewhat arbitrary requirement of the autograding system.

### Commit Specification    
1. Commit your modified code, config/meta files, and your custom message file as well any supporting files.

## Question 6: Using launch files
If you have been running your publisher(s), subscriber(s), and roscore separately using the rosrun command, there’s a more organized way to run multiple nodes at same time with one command.

In this exercise, we ask you to write a single launch file called `my_first_launch.launch` containing all 4 python files that you have written thus far.

### Commit Specification    
1. Commit your launch file. It should be inside a directory called `launch` within your package.

## Question 7: Use ROS parameters
When writing the last publisher (***fake_scan_publisher***), you had a couple of variables with default values including angle_min, angle_max, range_min, range_max, etc. With the current setup, if you want to change the value of one of those variables you will have to edit the Python code. For hundreds of lines of code, finding where each of such variables is defined can be tedious. The rosparam server provides a way to set those parameters on the terminal when running your program and in launch or config files. You task here is to parameterize the following variables from the last two nodes.

**Note:** Your node should be able to start (e.g. via `rosrun`) even if not all of these parameters have been set. If a parameter has not been set, your node should default to using the values given in the previous question. You will most likely want to use [`rospy.get_param`](http://wiki.ros.org/rospy/Overview/Parameter%20Server), which provides a mechanism for this. This way of falling back to hard-coded defaults can still be useful, especially in cases where a sensible default for a parameter is known and changes would only have to be made rarely.

1. Fake Scan Publisher     
	* Publish topic      
	* Publish rate      
	* Angle_min     
	* Angle_max     
	* Range_min      
	* Range_max     
	* Angle_increment      
2. Open Space Publisher     
	* Subscriber topic     
	* Publisher topic     

### Commit Specification
1. Commit your modified nodes along with any other important changes.

## Question 8: Playing with bag files
In question 3, we asked you to visualize your laserscan data on RViz and record a bag file. The RViz visualization was probably meaningless and ugly because you’re publishing random data. Don’t be alarmed; real laserscan data is a lot prettier and more informative. Download these [bagfiles](https://www.dropbox.com/s/17d25jtued10jk0/gmapping_data_active_only.zip?dl=0) follow the instructions [here](http://wiki.ros.org/ROS/Tutorials/Recording%20and%20playing%20back%20data), and visualize the laser scan data on RViz. Try it with multiple coordinate frames.     

**Note**: The provided bag files are from our cars driving around in the basement of Stata center.

## Question 9: Optional TF Exercises

For extra credit, complete the following exercises. You will need to download [this rosbag](https://www.dropbox.com/s/qvqloye6dilsj4y/tesse_no_statics_2.bag?dl=0) from Google drive; it may take a while.

The rosbag was collected from a robot driving around in a simulated environment. Its `base_link` position in the environment is broadcast to the TF tree in ROS. However, the poses of the sensors onboard the robot are not broadcasted to the TF tree.

Note that instead of `map`, this rosbag uses `world`. Instead of `base_link`, this rosbag uses `base_link_gt`.

* **MAKE SURE TO RESUBMIT YOUR REPO AS A ZIP FILE TO GRADESCOPE AFTER DOING THESE EXERCISES**
* **USE tf2_ros, NOT tf!!**

### Part 1: The Hard Way

Begin by developing a ROS node that publishes the correct TF of the left and right cameras to the TF tree. Name this node `dynamic_tf_cam_publisher.py`.

The left camera is located `0.05m` to the left of the `base_link_gt` position, and the right camera is located `0.05m` to the right of the `base_link_gt` position. Both cameras have identity rotation relative to the `base_link_gt` pose. In this case, the right-direction is the positive-x axis.

Precompute the relative transforms between the cameras and `base_link_gt` as 4x4 numpy arrays using the above information. Refer to lecture notes for the typical 4x4 formulation.

At each time step, your node should:

1. Get the current transform of the robot w.r.t. `world`. Use the TF tree!
2. Convert the robot's transform to a 4x4 numpy array.
3. Compute the current transform of the left camera w.r.t. **world** by composing the precomputed camera-base_link transform with the base_link-world transform.
4. Compute the current transform of the right camera w.r.t **the left camera** by composing the relevant matrices.
5. Broadcast the computed transforms for the cameras to the TF tree. The left camera's TF should be broadcast on the `left_cam` frame, and the right camera's TF goes on `right_cam`.

Save a short (~3-5 second) gif of RViz as the rosbag plays with your node running. Make sure we can see the base_link frame and both the left and right camera frames moving around. Name this file `dynamic_node.gif` and save it in the `ros_exercises/rviz` directory of your package.

Take a screen-shot of your tf tree in **rqt** using the `tf-tree` plugin. Save it in `ros_exercises/rqt` and name it `dynamic_tf_tree.png`

* **Note 1:** Don't worry if the new TF frames are jittery and/or don't follow the `base_link_gt` frame fast enough; this should be fixed in part 2.

* **Note 2:** You will be doing some transformations in your ROS node. Use [tf.transformations](http://docs.ros.org/jade/api/tf/html/python/transformations.html), a file built into the `tf` package. View the source code [here](https://github.com/ros/geometry/blob/melodic-devel/tf/src/tf/transformations.py). Also, use `numpy`!

* **Note 3:** Remember: your `left_cam` transform is defined relative to `world`, and your `right_cam` transform is defined relative to `left_cam`. These require slightly different equations!

* **Note 4:** You can easily record screen-captures using the Kazam package (`sudo apt-get install kazam`) and you can use the `ffmpeg` package (see [this](https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality) post) or a web-hosted tool to convert to gif.


### Part 2: The ~~Easy~~ Better Way

#### 2a: ROS Node

Write a ROS node that publishes the relative pose between each camera and the robot as a **static transform**. It should only broadcast the transform once. Name this node `static_tf_cam_publisher.py`. Make sure to use `tf2_ros`

Save a short (~3-5 second) gif of RViz just as in part 1, but with your `static_tf_cam_publisher.py` node running. Name this file `static_node.gif` and save it in the `ros_exercises/rviz` directory of your package. This should look much smoother than in part 1.

#### 2b: Launch File

Additionally, write a roslaunch file that launches the `static_transform_publisher` node from the `tf` package and automatically publishes the two transforms. Name this launch file `static_tf_publisher.launch` and save it in the `ros_exercises/launch` directory of your package.

If you're getting an "extrapolation into the future" error, add this to your launch file:

```bash
<param name="/use_sim_time" value="true"/>
```

And make sure you're running the rosbag with the `/clock` topic published like so:

```bash
rosbag play tesse_no_statics_2.bag --clock
```

See [here](https://answers.ros.org/question/288672/how-use_sim_time-works/) for more information.

* **Note 1:** Your launch file should not launch any of your nodes yet, just the `static_transform_publisher` node in the `tf` package.


### Part 3: Back to `base_link`

Write a new ROS node called `base_link_tf_pub.py`.

This new node must listen to the transform between `left_cam` and `world` and then broadcast the transform from `base_link_gt` to `world` on a new frame: `base_link_gt_2`. The transform you publish must be computed by composing the transform between `left_cam` and `base_link` with the transform you are listening for. In other words, this **cannot** be a static transform.

Add this node to your `static_tf_publisher.launch` file, such that both the static transforms for the two cameras are published when the launch file is executed. You should be able to visualize both `base_link_gt` and `base_link_gt_2` on top of each other in RViz.

Save a short gif of RViz again, and make sure you can see the both `base_link_gt_2` and `base_link_gt` on top of each other. Name this file `back_to_base_link.gif` and save it in the `ros_exercises/rviz` directory.

* **Tip:** Use `numpy.linalg.inv()`!


## Debugging Hints
Here are some helpful tools to use when trying to debugging your code.

Helpful debugging tools (once a node is running):

### `rostopic list`
A running node should be publishing or subscribing to different topics. To check that these topics are being listened/talked to, the command `rostopic list`, which will list all topics that are currently active (either being subscribed to, published to, or both).

### `rostopic echo /topic_name`
Once you know that a command is being published/subscribed to, you can echo its contents, which can show whether or not any information is being passed across this topic or if you are not sending what you expect.

### `rostopic hz /topic_name`
This command can tell you the rate at which messages are being published. This tool is helpful to verify if you are publishing messages at a certain frequency.

The ROS documentation for rostopic at http://wiki.ros.org/rostopic can provide many other tools to debug your ROS node setup.

### `rqt graph`
This is a tool to display graphs of running ROS nodes with connecting topics and package dependencies. Allows you to visualize your entire framework! Another helpful technique is to look at the [rqt_graph](http://wiki.ros.org/rqt_graph) which shows the interactions between nodes for your system.

### **`rviz`**
This is a powerful 3D visualization tool for displaying sensor data and state information from ROS. You will be using it more extensively in future labs.
