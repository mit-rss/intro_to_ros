| **Deliverable**  | **Due Date**                                 |
|---------------|----------------------------------------------------------------------------|
| `log.npf` and `lab1c.zip` on [Gradescope](https://www.gradescope.com/courses/973988) (listed as two separate assignments)| Wednesday, February 19th at 1:00PM EST |

# Lab 1C: Intro to ROS

## Table of Contents

* [Introduction](https://github.com/mit-rss/intro_to_ros#introduction)
* [Submission](https://github.com/mit-rss/intro_to_ros#submission)
	* [Automated Tests](https://github.com/mit-rss/intro_to_ros#automated-tests)
	* [Automatic Grade Breakdown](https://github.com/mit-rss/intro_to_ros#automatic-grade-breakdown)
 	* [Manual Grading Portion](https://github.com/mit-rss/intro_to_ros#manual-grading-portion)
	* [Manual Grade Breakdown](https://github.com/mit-rss/intro_to_ros#manual-grade-breakdown)
* [References](https://github.com/mit-rss/intro_to_ros#references)
* [ROS Exercises](https://github.com/mit-rss/intro_to_ros#ros-exercises)
	* [Create a Package and Build It](https://github.com/mit-rss/intro_to_ros#create-a-package-and-build-it)
	* [Question 1: Create Simple Publisher (Python)](https://github.com/mit-rss/intro_to_ros#question-1-create-simple-publisher-python)
	* [Question 2: Create Simple Subscriber (Python)](https://github.com/mit-rss/intro_to_ros#question-2-create-simple-subscriber-python)
	* [Question 3: Create More Complex Publisher (Python)](https://github.com/mit-rss/intro_to_ros#question-3-create-more-complex-publisher-python)
	* [Question 4: Create More Complex Subscriber (Python)](https://github.com/mit-rss/intro_to_ros#question-4-create-more-complex-subscriber-python)
	* [Question 5: Create a Custom Message and Publish It](https://github.com/mit-rss/intro_to_ros#question-5-create-a-custom-message-and-publish-it)
	* [Question 6: Using Launch Files](https://github.com/mit-rss/intro_to_ros#question-6-using-launch-files)
	* [Question 7: Use ROS Parameters](https://github.com/mit-rss/intro_to_ros#question-7-use-ros-parameters)
	* [Question 8: Playing with Bag Files](https://github.com/mit-rss/intro_to_ros#question-8-playing-with-bag-files)
	* [Question 9: TF Exercises](https://github.com/mit-rss/intro_to_ros#question-9-tf-exercises)
* [Debugging Hints](https://github.com/mit-rss/intro_to_ros#debugging-hints)
* [Frequently Used Instructions](https://github.com/mit-rss/frequently_used_instructions)

## Introduction

**Before this lab:** Make sure you have completed the [base installation](https://github.com/mit-rss/racecar_docker) of the racecar Docker container.

The objective of the following exercises is to help you practice the most commonly used concepts in ROS. We provide a quick reference document and pointers to relevant documentation. Feel free to use all the resources available to you to learn the concepts as thoroughly as possible and complete the exercises as efficiently as possible.

Although you're encouraged to collaborate with others if you are stuck, the lab should be completed individually so you can get practice with skills that will be essential later on in the course when you are in teams. If you have general questions, please post them on Piazza so other students can benefit from the answer. If you have a question about your individual submission, please make a private post.

## Submission

You are meant to complete this lab by testing your code and verifying the results on your own, as you would do in real life. Once you are confident in your answers, your lab will be graded against our automated tests. Please refer to the next section, **Automated Tests** for instructions on how to run these tests. You will be submitting the resulting `log.npf` file to **Lab 1C: Intro to ROS -- log.npf submission** on Gradescope, in addition to a zip file containing your local repository (`lab1c.zip`) to **Lab 1C: Intro to ROS -- Git repo submission**.

The due date is listed at the top of this document.

### Automated Tests 

You can download the test binary to check your solutions locally by going to the [release page here](https://github.com/mit-rss/intro_to_ros/releases) and downloading the `run_tests` binary.
Most people will probably need to use the `amd64` version but if your Mac's chip is M1-M3, you'll need to use the `arm64` version. **Make sure you place the binary in your `ros_exercises` folder**:

```
mv run_tests_* ~/racecar_ws/src/lab1c/ros_exercises/
```

Then make the binary executable with `chmod`

```
chmod +x run_tests_*
```

Finally, run the following in a new terminal to begin testing:

```
cd ~/racecar_ws/src/lab1c/ros_exercises/
./run_tests_*
```

You should be graded on the completion of 6 tests. Be careful with naming the various files defined in the handout correctly or else you won't be graded properly. Also, **be sure to `cd` into `ros_exercises` before running the tests**, or the automated tests may use the wrong paths to each of the files it checks for. Once you are happy with your score, submit the resulting `log.npf` file to **Lab 1C: Intro to ROS -- log.npf submission** on Gradescope.

### Automatic Grade Breakdown

This table shows how the different tasks will be graded by the automated grader.
| Task                    |      Grade        |
|-------------------------|-------------------|
| Simple Publisher        |      0.5 points   |
| Simple Subscriber       |      0.5 Points   |
| Complex Publisher       |      0.5 Points   |
| Complex Subscriber      |      0.5 Points   |
| Launch File             |      0.5 Points   |
| **Total**               |   **2.5 Points**  |

### Manual Grading Portion

Submit a zip file of your `lab1c` repository to the Gradescope assignment **Lab 1C: Intro to ROS -- Git repo submission**. Make sure that your zip file does not contain large folders or files that are not part of the assignments (the **.git** folder should not be zipped) since large zip files will probably get rejected by Gradescope. 

### Manual Grade Breakdown
This table shows the grading breakdown of the manually graded portion of the lab.
| Task                                | Grade          |
|-------------------------------------|----------------|
| Simple Publisher RQT Screenshot     | 0.1 Points     |
| Simple Subscriber RQT screenshot    | 0.1 Points     |
| Fake Scan RViz ScreenShot           | 0.1 Points     |
| Open Space Publisher RQT Screenshot | 0.1 Points     |
| Custom Message file inspection      | 0.1 Points     |
| Launch file inspection              | 0.1 Points     |
| Setting  ROS parameters	      | 0.1 Points     |
| TF Exercises                        | 0.8 Points     |
| **Total**                           | **1.5 Points** |

## References

The following are selected chapters from the ROS2 [Documentation](https://docs.ros.org/en/foxy/index.html) and [Tutorials](https://docs.ros.org/en/foxy/Tutorials.html). If you understand all the concepts covered in these exercises, you will be ready for the exercises of this lab (given below) and most of the ROS-related tasks you will be performing throughout the first few labs.

Additionally, a useful ROS cheatsheet can be found [here](https://github.com/Micropolisdxb/ROS2-Documentation/blob/main/ros2_cheat_sheet.md).

**Note:** We are using ROS **FOXY** and colcon for this class. Make sure the documentation you are looking at is for the correct build/distribution.
 
1. Packages   
	a. [Managing a colcon workspace](https://docs.ros.org/en/foxy/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html)    
	b. [Create ROS python package](https://docs.ros.org/en/foxy/How-To-Guides/Developing-a-ROS-2-Package.html#python-packages)    
2. Messages   
	a. [ROS Messages](https://docs.ros.org/en/foxy/Concepts/About-ROS-Interfaces.html)   
	b. [Creating custom messages](https://docs.ros.org/en/foxy/Tutorials/Beginner-Client-Libraries/Custom-ROS2-Interfaces.html)    
	c. [Common ros message categories](https://github.com/ros2/common_interfaces)   
4. Nodes   
	a. [ROS Nodes](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)   
	b. [Writing Publisher and Subscriber(Python)](https://docs.ros.org/en/foxy/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html )   
3. [Topics](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html)  
5. Launch Files    
	a. [ROS Launch](https://docs.ros.org/en/foxy/Tutorials/Intermediate/Launch/Launch-Main.html)   
	b. [Launch system](https://docs.ros.org/en/foxy/Tutorials/Intermediate/Launch/Launch-system.html)  
6. [Parameters](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Parameters/Understanding-ROS2-Parameters.html)   
7. Visualization Tools 	  
	a. rqt   
		- [rqt](https://docs.ros.org/en/foxy/Concepts/About-RQt.html)   
		- [rqt_graph](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html#rqt-graph)   
	b. [RViz](https://docs.ros.org/en/humble/Tutorials/Intermediate/RViz/RViz-User-Guide/RViz-User-Guide.html)

8. [TF2](https://docs.ros.org/en/foxy/Tutorials/Intermediate/Tf2/Tf2-Main.html)   
9. [Rosbag](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html)  

**Note:** Some useful debugging hints are provided at the end of this document.

## ROS Exercises

### Create a Package and Build It

The racecar docker image already has a workspace installed called `racecar_ws`. 

If you are not using docker to run ROS (e.g. using a virtual machine or a manual install), make sure to create your own workspace.

Inside your workspace, create a new PYTHON BASED (not C++ based) package (this means that the keyword **ament_python** will be in the command to create the package), named `ros_exercises/`, which should depend on `rclpy`, `std_msgs`, and `sensor_msgs`. Your package (`ros_exercises`) should live in the `~/racecar_ws/src/lab1c/` directory. Make `lab1c` a git repo, and have it track `ros_exercises` and `custom_msgs` (later on). After creating the workspace and the package, you should have the following directory layout.

```
~/racecar_ws (your colcon workspace)
├── src
|   ├── lab1c (init git here)
|   |   ├── ros_exercises (your package)
|   |   └── custom_msgs (created later)
|   └── (other ros related files and packages if any)
├── install (auto-generated during build)
├── log (auto-generated during build)
└── build (auto-generated during build)
```

Every time you add a file or make a new package, make sure to run `colcon build --symlink-install` to build your package. **ALWAYS** run this command from the `~/racecar_ws` directory. If you run `colcon build --symlink-install` from a different directory, delete the auto-generated `install`, `log` and `build` directories. Additionally, whenever you open a new terminal or run `colcon build --symlink-install`, **source your `setup.bash` file** so you use the underlaid build of your package.

```
source install/setup.bash
```    
   
**Note**: Push your `ros_exercises/` changes to github.

### Question 1: Create Simple Publisher (Python)
Your task in this exercise is to create a simple ROS node that publishes a random number between 0.0 and 10.0. Note that this file will reside inside of the `ros_exercises/ros_exercises/` folder (i.e. inside the `ros_exercises/` folder in your `ros_exercises` package).

#### Node Specification    
- **Description:** Publishes a random number between 0 and 10.    
- **File name:** simple_publisher.py    
- **Node Name:** simple_publisher
- **Published topic names:** my_random_float    
- **Message type:** Float32    
- **Subscription topic names:** None    
- **Publish rate:** 20hz    

#### Commit Specification    
1. When your node works properly, run it (remember to update your `setup.py`, `colcon build --symlnk-install`, and `source install/setup.bash`), take a screenshot of ***rqt_graph*** visualization of your node(s) and topic(s). Name your screenshot `simple_publisher_rqt.png` and save it in `ros_exercises/rqt/` (create the `rqt/` directory). Note: `ros_exercises/` is the ROS package you created at the beginning of this section.
2. Push your code, the screenshot, and any supporting files with an appropriate commit message.

**For grading purposes: ALWAYS NAME THE SCRIPT EXECUTABLE'S NAME THE SAME AS ITS CORRESPONDING NODE'S NAME**

### Question 2: Create Simple Subscriber (Python)
In this exercise, you will write a listener (subscriber) that listens to the topic `my_random_float`, which is published by the previous node. The new node takes the natural log of the message in the `my_random_float` topic and publishes it to `random_float_log`.

#### Node Specification
- **Description:** Subscribes to the topic published on by the simple_publisher and publishes the natural log of the received messages.
- **File name:** simple_subscriber.py
- **Node Name:** simple_subscriber
- **Published topic names:** random_float_log
- **Message type:** Float32
- **Subscription topic names:** my_random_float

#### Commit Specification
1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, name it `simple_subscriber_rqt.png`, and save it in the same folder as the previous exercise.
2. Again, push your code, the screenshot, and any supporting files with an appropriate commit message.

### Question 3: Create More Complex Publisher (Python)
In this exercise, you will write a node that publishes fake laser scan data as specified below. Additionally, you will publish the length of the `ranges` array of the LaserScan message.

#### Node Specification    
- **Description:** Publish a [LaserScan](https://docs.ros2.org/latest/api/sensor_msgs/msg/LaserScan.html) message with random ranges between 1.0 and 10.0. Also publish a Float32 message with the length of the `ranges` array.
- **File name:** fake_scan_publisher.py
- **Node Name:** fake_scan_publisher
- **Published topic names:** fake_scan, range_test
- **Message type:** LaserScan, Float32 (respectively)
- **Subscription topic names:** None   
- **Publish Rate:** 20hz

>**Note:** ROS is very particular about its message types. Make sure you convert the length of the `ranges` array to a `float` before publishing.

#### LaserScan Topic Specifications
- **Header:**       
	- **Timestamp:** Current ROS time
	- **Frame_id:** `base_link`
- **Angle_min:** (-2/3)*pi*     
- **Angle_max:** (2/3)*pi*     
- **Angle_increment:** (1/300)*pi*     
- **Time_increment:** Leave it unset if you wish
- **Scan_time:** The time difference in seconds between consecutive scans.
- **Range_min:** 1.0
- **Range_max:** 10.0
- **Ranges:** One dimensional array with elements of random floats between range_min and range_max, Use angle_min, angle_max,  and angle_increment to determine the length. Be careful of an off-by-1 error! There should be an element **at** ```angle_min``` and ```angle_max```.
- **Intensities:** Leave it unset if you wish

#### Commit Specification   
1. When your node works properly, visualize the published laser scan data using RViz. Take a screenshot of your visualized laser scan data and name it `fake_scan_rviz.png`. Save the image in `ros_exercises/rviz`. If you can't see anything in `rviz` it's probably because you're publishing your laser scan message with the header `base_link` but rviz is visualizing relative to the frame `map`. In the panel on the left, under global options change `Fixed Frame: map` to `Fixed Frame: base_link`.
2. Record a ~10-second [bag](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html) file of your laser scan data and call the file `fake_scan_bag`, save it in `ros_exercises/rosbag`.
3. Again, push your code, bag file, screenshot, and any supporting files with an appropriate commit message.

**If you are failing this test make sure you have these files and directories in your `ros_exercises` directory**:
- `rviz/fake_scan_rviz.png`
- `rosbag/fake_scan_bag/`

### Question 4: Create More Complex Subscriber (Python)
Create a node that subscribes to the fake laser scan data and outputs the longest range from the laser scan ranges and its corresponding angle.

#### Node Specification
- **Description:** Subscribes to the fake_scan topic published on by the fake_scan_publisher from the previous exercises, and finds the longest return (the range element with the greatest value) and publishes the corresponding angle and return value or distance.
- **File name:** open_space_publisher.py
- **Node Name:** open_space_publisher
- **Published topic names:** `open_space/distance` and `open_space/angle`
- **Message type:** Float32
- **Subscription topic names:** fake_scan

#### Commit Specification
1. Again, take a screenshot of ***rqt_graph*** showing your nodes running, named it `open_space_rqt.png`, and save it in `ros_exercises/rqt`.
2. Again, push your code, the screenshot, and any supporting files with an appropriate commit message.

**If you are failing this test make sure you have these files in your ```ros_exercises``` directory**:
- ```rqt/open_space_rqt.png```

Note: Test case #4 and onward will still not pass. You will need to finish Question 5 to pass the next test case.

### Question 5: Create a Custom Message and Publish It
The publisher from the previous exercise was publishing two related pieces of data on two separate topics (***open_space/angle*** and ***open_space/distance***). In this exercise, we ask you to create a custom message that encapsulates the two pieces of data, the same way the LaserScan message type combines multiple pieces of data. Create a new `custom_msgs` CMake package containing your custom message file `OpenSpace.msg`. After creating and compiling your custom message, modify the publisher from the previous exercise to publish this message type on the topic `open_space`.

**Important:** For grading purposes, it is required that your `angle` field be specified **BEFORE** your `distance` field. When creating your messages, you will be completely in charge of what your message specification looks like, so be aware that this is just a somewhat arbitrary requirement of the auto-grading system.

#### Commit Specification    
1. Commit your modified code, config/meta files, and your custom message file as well as any supporting files.

### Question 6: Using Launch Files
If you have been running your publisher(s) and subscriber(s) separately using the `ros2 run` command, there's a more organized way to run multiple nodes at the same time with one command.

In this exercise, we ask you to write a single launch file called `my_first_launch.launch.xml` containing all 4 python files that you have written thus far.

#### Commit Specification    
1. Commit your launch file. It should be inside a directory called `launch` within your package.

### Question 7: Use ROS Parameters
When writing the last publisher (`fake_scan_publisher`), you had a couple of variables with default values including angle_min, angle_max, range_min, range_max, etc. With the current setup, if you want to change the value of one of those variables you will have to edit the Python code. For hundreds of lines of code, finding where each of such variables is defined can be tedious. The rosparam server provides a way to set those parameters on the terminal when running your program and in launch or config files. Your task here is to parameterize the following variables from the last two nodes.

**Note:** Your node should be able to start (e.g. via `ros2 run`) even if not all of these parameters have been set. If a parameter has not been set, your node should default to using the values given in the previous question. This [link](https://roboticsbackend.com/rclpy-params-tutorial-get-set-ros2-params-with-python/) may be helpful. This way of falling back to hard-coded defaults can still be useful, especially in cases where a sensible default for a parameter is known and changes would only have to be made rarely.

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

#### Commit Specification
1. Commit your modified nodes along with any other important changes.

### Question 8: Playing with Bag Files
In question 3, we asked you to visualize your laserscan data on RViz and record a bag file. The RViz visualization was probably meaningless and ugly because you’re publishing random data. Don’t be alarmed; real laserscan data is a lot prettier and more informative. Download these [bagfiles](https://www.dropbox.com/scl/fi/z4ln37mh9twxmpzu7obx1/gmapping_data_active_only.zip?rlkey=nxiyhgfo2396acwxoztqbuo4k&dl=0), follow the instructions [here](https://docs.ros.org/en/foxy/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html), and visualize the laser scan data on RViz. Try it with multiple coordinate frames.     

**Note**: The provided bag files are from our cars driving around in the basement of Stata Center.

### Question 9: TF Exercises

In this question, we will use the `one_loop` bagfile from Question 8. Note that instead of `map`, this rosbag uses `odom`.

#### Part 1: The Hard Way

Begin by developing a ROS node that publishes the correct TF of the left and right cameras to the TF tree. Name this node `dynamic_tf_cam_publisher.py`.

The left camera is located `0.05m` to the left of the `base_link` position, and the right camera is located `0.05m` to the right of the `base_link` position. Both cameras have identity rotation relative to the `base_link` pose. In this case, the "forward" direction is the positive-x axis, and the "left" direction is the positive-y axis.

Precompute the relative transforms between the cameras and `base_link` as 4x4 numpy arrays using the above information. Refer to lecture notes for the typical 4x4 formulation.

At each time step, your node should:

1. Get the current transform of the robot w.r.t. (with respect to) `odom`. Use the TF tree!
2. Convert the robot's transform to a 4x4 numpy array.
3. Compute the current transform of the left camera w.r.t. `odom` by composing the precomputed `base_link->camera` transform with the `odom->base_link` transform.
4. Compute the current transform of the right camera w.r.t **the left camera** by composing the relevant matrices.
5. Broadcast the computed transforms for the cameras to the TF tree. The left camera's TF should be broadcast on the `left_cam` frame, and the right camera's TF goes on `right_cam`.

Save a short (~3-5 second) gif of RViz as the rosbag plays with your node running. Since this bagfile uses the `odom` frame, you need to click the panel on the left and under global options, change `Fixed Frame: map` to `Fixed Frame: odom`.
This changes the "origin" of the RViz grid to the `odom` frame instead of the `map` frame which doesn't exist in this bagfile. Additionally, make sure we can see the `base_link` frame and both the left and right camera frames moving around
by clicking `Add -> By display type -> TF`. Finally, we can make the camera follow `base_link` by changing `Target Frame: <Fixed Frame>` to `Target Frame: base_link` on the right panel. Name this gif `dynamic_node.gif` and save it in the `ros_exercises/rviz` directory of your package.

Take a screenshot of your tf tree using `ros2 run tf2_tools view_frames.py`. Save the resulting PDF in `ros_exercises/rqt` and name it `dynamic_tf_tree.pdf` (you can delete the `frames.gv` file).

* **Note 1:** Don't worry if the new TF frames are jittery and/or don't follow the `base_link` frame fast enough; this should be fixed in part 2.
* **Note 2:** You will be doing some transformations in your ROS node. **Use [tf_transformations](https://github.com/DLu/tf_transformations/blob/main/README.md)**, a library that can convert transformations between Euler angles, quaternions, and matrices.
* **Note 3:** Remember: your `left_cam` transform is defined relative to `odom`, and your `right_cam` transform is defined relative to `left_cam`. These require slightly different equations!
* **Note 4:** You can easily record screen captures using the Kazam package (`sudo apt-get install kazam`) and you can use the `ffmpeg` package (see [this](https://superuser.com/questions/556029/how-do-i-convert-a-video-to-gif-using-ffmpeg-with-reasonable-quality) post) or a [web-hosted tool](https://new.express.adobe.com/tools/convert-to-gif) to convert to gif.

#### Part 2: The ~~Easy~~ Better Way

#### 2a: ROS Node

Write a ROS node that publishes the relative pose between each camera and the robot as a **static transform**. The static transforms to broadcast are `base_link->left_cam` and `left_cam->right_cam`.
The node should only broadcast each transform once. Name this node `static_tf_cam_publisher.py`.

Save a short (~3-5 seconds) gif of RViz just as in part 1, but with your `static_tf_cam_publisher.py` node running. Name this file `static_node.gif` and save it in the `ros_exercises/rviz` directory of your package. This should look much smoother than in part 1.

#### 2b: Launch File

Write a roslaunch file that runs `static_tf_cam_publisher.py`. Name this launch file `static_tf_publisher.launch.xml` and save it in the `ros_exercises/launch` directory of your package.

#### Part 3: Back to `base_link`

Write a new ROS node called `base_link_tf_pub.py`.

This new node must listen to the transform between `left_cam` and `odom` and then broadcast the transform from `odom` to `base_link` on a new frame: `base_link_2`. The transform you publish must be computed by composing the transform between `left_cam` and `base_link` with the transform you are listening for. In other words, this **cannot** be a static transform.

Add this node to your `static_tf_publisher.launch.xml` file, such that both the static transforms for the two cameras are published when the launch file is executed. You should be able to visualize both `base_link` and `base_link_2` on top of each other in RViz.

Save a short gif of RViz again, and make sure you can see both `base_link_2` and `base_link` on top of each other. Name this file `back_to_base_link.gif` and save it in the `ros_exercises/rviz` directory.

* **Hint:** Use `numpy.linalg.inv()`!

## Debugging Hints
Here are some helpful tools to use when trying to debug your code.

Helpful debugging tools (once a node is running):

### `ros2 topic list`
A running node should be publishing or subscribing to different topics. To check that these topics are being listened/talked to, the command `rostopic list` will list all topics that are currently active (either being subscribed to, published to, or both).

### `ros2 topic echo /topic_name`
Once you know that a command is being published/subscribed to, you can echo its contents, which can show whether or not any information is being passed across this topic or if you are not sending what you expect.

### `rqt_graph`
This is a tool to display graphs of running ROS nodes with connecting topics and package dependencies. Allows you to visualize your entire framework! 

### **`rviz2`**
This is a powerful 3D visualization tool for displaying sensor data and state information from ROS. You will be using it more extensively in future labs.

### **`ros2 run tf2_tools view_frames.py`**
This creates a PDF file with a visualization of your TF tree.

To find more ways to use ```ros2 topic```, type ```ros2 topic --help``` in the command line. There are many other helpful command line tools to help you out too. See [here](https://docs.ros.org/en/foxy/Concepts/About-Command-Line-Tools.html).

