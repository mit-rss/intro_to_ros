| Deliverable                                                                                           | Due Date                             |
|-------------------------------------------------------------------------------------------------------|--------------------------------------|
| `log.npf` [Gradescope Submission](https://www.gradescope.com/courses/1227626/assignments/7471281)     | Tuesday, February 17th at 1:00PM EST |
| Manual grader [Gradescope Submission](https://www.gradescope.com/courses/1227626/assignments/7574354) | Tuesday, February 17th at 1:00PM EST |

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
    * [Question 1: Create a Simple Publisher (Python)](https://github.com/mit-rss/intro_to_ros#question-1-create-a-simple-publisher-python)
    * [Question 2: Create a Simple Subscriber (Python)](https://github.com/mit-rss/intro_to_ros#question-2-create-a-simple-subscriber-python)
    * [Question 3: Create a More Complex Publisher (Python)](https://github.com/mit-rss/intro_to_ros#question-3-create-a-more-complex-publisher-python)
    * [Question 4: Create a More Complex Subscriber (Python)](https://github.com/mit-rss/intro_to_ros#question-4-create-a-more-complex-subscriber-python)
    * [Question 5: Create a Custom Message and Publish It](https://github.com/mit-rss/intro_to_ros#question-5-create-a-custom-message-and-publish-it)
    * [Question 6: Using Launch Files](https://github.com/mit-rss/intro_to_ros#question-6-using-launch-files)
    * [Question 7: Use ROS Parameters](https://github.com/mit-rss/intro_to_ros#question-7-use-ros-parameters)
    * [Question 8: Playing with Bag Files](https://github.com/mit-rss/intro_to_ros#question-8-playing-with-bag-files)
    * [Question 9: TF Exercises](https://github.com/mit-rss/intro_to_ros#question-9-tf-exercises)
* [Debugging Hints](https://github.com/mit-rss/intro_to_ros#debugging-hints)
* [Frequently Used Instructions](https://github.com/mit-rss/frequently_used_instructions)

## Introduction

**Before this lab:** Make sure you have completed the [base installation](https://github.com/mit-rss/racecar_docker) of the racecar Docker container.

The objective of the following exercises is to help you practice the most commonly used concepts in ROS. We provide a quick reference document
and pointers to relevant documentation. Feel free to use all the resources available to you to learn the concepts as thoroughly as possible and
complete the exercises as efficiently as possible.

Although you're encouraged to collaborate with others if you are stuck, the lab should be completed individually so you can get practice
with skills that will be essential later on in the course when you are in teams. If you have general questions, please post them on
[Piazza](https://piazza.com/mit/spring2026/64200164052124/home) so other students can benefit from the answer. If you have a question
about your individual submission, please make a private post.

## Submission

You are meant to complete this lab by testing your code and verifying the results on your own, as you would do in real life.
Once you are confident in your answers, your lab will be graded against our automated tests. Please refer to the next section,
**Automated Tests** for instructions on how to run these tests. You will be submitting the resulting `log.npf` file to
**Lab 1C: Intro to ROS -- log.npf submission** on Gradescope in addition to your code, screenshot, and videos to
**Lab 1C: Intro to ROS -- Manual grader**.

### Automated Tests 

You can download the test binary to check your solutions locally by going to the [release page](https://github.com/mit-rss/intro_to_ros/releases)
and downloading the `run_tests` binary. **Run this autograder AFTER you have completed questions 1-6**. Most people will probably need to use
the `amd64` version, but if you have an Apple Silicon chip, you'll need to use the `arm64` version.

Once you download the test binary, make it executable with `chmod`:
```
chmod +x run_tests_*
```

Finally, run the following in a new terminal to begin testing:
```
./run_tests_*
```

You should be graded on the completion of 6 tests. Once you are happy with your score, submit the resulting `log.npf` file
to **Lab 1C: Intro to ROS -- log.npf submission** on Gradescope.

### Automatic Grade Breakdown

This table shows how the different tasks will be graded by the automated grader.

| Task                                   | Grade          |
|----------------------------------------|----------------|
| Create a Simple Publisher              | 0.5 points     |
| Create a Simple Subscriber             | 0.5 Points     |
| Create a More Complex Publisher        | 0.5 Points     |
| Create a More Complex Subscriber       | 0.5 Points     |
| Create a Custom Message and Publish It | 0.5 Points     |
| Using Launch Files                     | 0.5 Points     |
| **Total**                              | **3.0 Points** |

### Manual Grading Portion

Throughout the exercises, submit your screenshots, videos, and code to the Gradescope assignment
**Lab 1C: Intro to ROS -- Manual grader** whenever a problem requests submission.

### Manual Grade Breakdown

This table shows the grading breakdown of the manually graded portion of the lab.

| Task                                   | Grade          |
|----------------------------------------|----------------|
| Create a Simple Publisher              | 0.1 Points     |
| Create a Simple Subscriber             | 0.4 Points     |
| Create a More Complex Publisher        | 0.2 Points     |
| Create a Custom Message and Publish It | 0.2 Points     |
| Using Launch Files                     | 0.3 Points     |
| Use ROS Parameters                     | 0.3 Points     |
| Playing with Bag Files                 | 0.3 Points     |
| TF Exercises                           | 3.2 Points     |
| **Total**                              | **5.0 Points** |

## References

The following are selected chapters from the ROS2 [Documentation](https://docs.ros.org/en/humble/index.html) and
[Tutorials](https://docs.ros.org/en/humble/Tutorials.html). If you understand the concepts covered in these tutorials, you will be
ready for the exercises of this lab and most of the ROS-related tasks you will be performing throughout the first few labs.

Additionally, a useful ROS2 cheatsheet can be found [here](https://github.com/Micropolisdxb/ROS2-Documentation/blob/main/ros2_cheat_sheet.md).

> This class uses ROS2 **Humble** with colcon. Be careful when searching online: much of the available documentation
> is for the deprecated ROS1 system, which uses different commands and concepts. Always verify you're reading ROS2 Humble documentation.
 
1. Packages
    a. [Managing a colcon workspace](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html)
    b. [Create a ROS Python package](https://docs.ros.org/en/humble/How-To-Guides/Developing-a-ROS-2-Package.html#python-packages)
2. Messages
    a. [ROS messages](https://docs.ros.org/en/humble/Concepts/About-ROS-Interfaces.html)
    b. [Creating custom messages](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Custom-ROS2-Interfaces.html)
    c. [Common ROS message categories](https://github.com/ros2/common_interfaces)
3. [Topics](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html)
4. Nodes
    a. [ROS nodes](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)
    b. [Writing publishers and subscribers (Python)](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html)
5. Launch Files
    a. [ROS launch](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Launch-Main.html)
    b. [Launch system](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Launch-system.html)
6. [Parameters](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Parameters/Understanding-ROS2-Parameters.html)
7. Visualization Tools
    a. [rqt](https://docs.ros.org/en/humble/Concepts/About-RQt.html)
    b. [rqt_graph](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html#rqt-graph)
    c. [RViz](https://docs.ros.org/en/humble/Tutorials/Intermediate/RViz/RViz-User-Guide/RViz-User-Guide.html)
8. [TF2](https://docs.ros.org/en/humble/Tutorials/Intermediate/Tf2/Tf2-Main.html)
9. [Rosbag](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html)

**Note:** Some useful debugging hints are provided at the end of this document.

## ROS Exercises

### Create a Package and Build It

The racecar Docker image already has a workspace installed called `racecar_ws`. 

If you are not using Docker to run ROS (e.g. using a virtual machine or a manual install), make sure to create your own workspace.

Inside your workspace, create a directory inside `/src` named `lab1c`. Inside this new `lab1c` directory, create a new
**Python based** (not C++ based) package (this means that the keyword **`ament_python`** will be in the command to create the package),
named `ros_exercises`, which should depend on `rclpy`, `std_msgs`, and `sensor_msgs`. Your `ros_exercises` package should live in the
`~/racecar_ws/src/lab1c/` directory.

```
~/racecar_ws (your colcon workspace)
├── src
|   ├── lab1c
|   |   ├── ros_exercises (your package)
|   |   └── custom_msgs (created later)
|   └── (other ros related files and packages if any)
├── install (auto-generated during build)
├── log (auto-generated during build)
└── build (auto-generated during build)
```

Every time you add a file or make a new package, make sure to run `colcon build --symlink-install` to build your package.
**ALWAYS** run this command from the `~/racecar_ws` directory. If you run `colcon build --symlink-install` from a different directory,
delete the auto-generated `install`, `log` and `build` directories. Additionally, whenever you open a new terminal or run
`colcon build --symlink-install`, **source your `setup.bash` file** so you use the underlaid build of your package:

```
source install/setup.bash
```

### Question 1: Create a Simple Publisher (Python)

Your task in this exercise is to create a simple ROS node that publishes a random number between 0.0 and 10.0. Note that this file
will reside inside of the `ros_exercises/ros_exercises/` folder (i.e. inside the `ros_exercises/` folder in your `ros_exercises` package).

#### Node Specification    

- **Description:** Publishes a random number between 0 and 10.
- **File name:** `simple_publisher.py`
- **Node Name:** `simple_publisher`
- **Published topic names:** `my_random_float`
- **Message type:** Float32
- **Subscription topic names:** None
- **Publish rate:** 20hz

When your node works properly, run it (remember to update your `setup.py`, `colcon build --symlink-install`, and `source install/setup.bash`),
take a screenshot of an **rqt_graph** visualization of your node(s) and topic(s), and upload the screenshot to Gradescope.

> **IMPORTANT NOTE:** For grading purposes, always name the script executable's name the same as its corresponding node's name.

### Question 2: Create a Simple Subscriber (Python)

In this exercise, you will write a listener (subscriber) that listens to the topic `my_random_float`, which is published by the previous node.
The new node takes the natural log of the message in the `my_random_float` topic and publishes it to `random_float_log`.

#### Node Specification

- **Description:** Subscribes to the topic published on by the `simple_publisher` and publishes the natural log of the received messages.
- **File name:** `simple_subscriber.py`
- **Node Name:** `simple_subscriber`
- **Published topic names:** `random_float_log`
- **Message type:** Float32
- **Subscription topic names:** `my_random_float`

Let's run both the subscriber and the publisher at the same time using `tmuxp`! Create a YAML tmux configuration file named
`simple_pubsub_tmux.yaml`. Running `tmuxp load simple_pubsub_tmux.yaml` launches a tmux session with the following structure:

- **Session name:** `rss_lab1c`
- **Window name:** `simple_pubsub`
- **Layout**: tiled
- **Pane 1:** runs the `simple_publisher` node
- **Pane 2:** runs the `simple_subscriber` node
- **Pane 3:** runs the command `ros2 topic echo /my_random_float`
- **Pane 4:** runs the command `ros2 topic hz /my_random_float`

On the bottom-left pane, you should see the output of `ros2 topic echo /my_random_float`. This is a valuable debugging tool
that lets you monitor messages on any topic in real-time, helping you verify that nodes are publishing correctly, check message
content and frequency, and troubleshoot communication issues between nodes.

On the bottom-right pane, `ros2 topic hz /my_random_float` monitors the message publishing frequency, which can be useful for
confirming your node is publishing at the expected rate and diagnosing timing issues. If you wrote `simple_publisher` correctly,
you should see your node is publishing `/my_random_float` at 20 Hz.

Take and save a screenshot of **rqt_graph** showing your nodes running. On rqt_graph, select `Nodes/Topics (all)` on the top-left to
view both nodes and topics, and uncheck the hide `Dead sinks` and `Leaf topics` options.

Lastly, take and save a screenshot of **rqt_plot**, selecting `/random_float_log/data` as the Topic on the top-left corner of the window.
rqt_plot is a tool that visualizes ROS2 topic data as a line graph, allowing you to see how values change over time. This is especially
useful for future labs with briefings and reports, where presenting quantitative data is essential.

Upload the rqt_graph screenshot, rqt_plot screenshot, and `simple_pubsub_tmux.yaml` to Gradescope.

> **Hint:** You can run rqt_plot using `ros2 run rqt_plot rqt_plot`.

### Question 3: Create a More Complex Publisher (Python)

In this exercise, you will write a node that publishes fake LaserScan data as specified below. Additionally, you will publish the
length of the `ranges` array of the LaserScan message.

#### Node Specification

- **Description:** Publish a [LaserScan](https://docs.ros2.org/latest/api/sensor_msgs/msg/LaserScan.html) message with random ranges
    between 1.0 and 10.0. Also publish a Float32 message with the length of the `ranges` array.
- **File name:** `fake_scan_publisher.py`
- **Node Name:** `fake_scan_publisher`
- **Published topic names:** `fake_scan`, `range_test`
- **Message type:** LaserScan, Float32 (respectively)
- **Subscription topic names:** None
- **Publish Rate:** 20hz

> ROS is very particular about its message types. Make sure you convert the length of the `ranges` array to a `float` before publishing.

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
- **Ranges:** One dimensional array with elements of random floats between `range_min` and `range_max`. Use `angle_min`, `angle_max`,
    and `angle_increment` to determine the length. Be careful of an off-by-1 error! There should be an element **at** `angle_min` and `angle_max`.
- **Intensities:** Leave it unset if you wish

When your node works properly, visualize the published LaserScan data using RViz. Take a screenshot of your visualized LaserScan data
and upload it to Gradescope.

> If you can't see anything in RViz, it's probably because you're publishing your LaserScan message with the header `base_link`
> but RViz is visualizing relative to the `map` frame. In the panel on the left, under global options, change `Fixed Frame: map`
> to `Fixed Frame: base_link`.

### Question 4: Create a More Complex Subscriber (Python)

Create a node that subscribes to the fake LaserScan data and outputs the longest range from the LaserScan ranges and its corresponding angle.

#### Node Specification

- **Description:** Subscribes to the `fake_scan` topic published by the `fake_scan_publisher` from the previous exercise,
    finds the range element with the greatest value, and publishes the value with its corresponding angle.
- **File name:** `open_space_publisher.py`
- **Node Name:** `open_space_publisher`
- **Published topic names:** `open_space/distance` and `open_space/angle`
- **Message type:** Float32
- **Subscription topic names:** `fake_scan`

### Question 5: Create a Custom Message and Publish It

In the previous exercise, the publisher sent two related data points on separate topics: `open_space/angle` and `open_space/distance`.
For this exercise, you'll create a custom message that bundles both pieces of data together, similar to how the LaserScan message type
consolidates multiple data fields. Start by creating a new CMake package called `custom_msgs` that contains your custom message file
`OpenSpace.msg`. `OpenSpace.msg` should include two Float32 fields: `angle` and `distance`. Once you've created and compiled this custom
message, update the publisher from the previous exercise to publish this new message type on a single topic called `open_space`,
replacing the two separate topic publications.

Take a screenshot of **rqt_graph** showing both `fake_scan_publisher.py` and `open_space_publisher.py`
running. Again, select `Nodes/Topics (all)` to view both nodes and topics, and uncheck the hide `Dead sinks` and
`Leaf topics` options. Upload the screenshot and `OpenSpace.msg` to Gradescope.

### Question 6: Using Launch Files

If you have been running your publisher(s) and subscriber(s) separately using the `ros2 run` command, there's a more organized way
to run multiple nodes at the same time with one command.

In this exercise, we ask you to write a single launch file called `my_first_launch.launch.xml` which launches all four nodes that
you have written thus far. Once completed, upload `my_first_launch.launch.xml` to Gradescope.

### Question 7: Use ROS Parameters

When writing the last publisher (`fake_scan_publisher`), you had a couple of variables with default values including `angle_min`,
`angle_max`, `range_min`, `range_max`, and `angle_increment`. With the current setup, if you want to change the value of one of those variables,
you will have to edit the Python code. For hundreds of lines of code, finding where each of such variables is defined can be tedious.
The rosparam server provides a way to set those parameters in the terminal, in launch files, and/or in config files. Your task
here is to parameterize the following variables from the last two nodes:

1. Fake Scan Publisher
	* Publish rate
	* `fake_scan` topic
	* `angle_min`
	* `angle_max`
	* `range_min`
	* `range_max`
	* `angle_increment`
2. Open Space Publisher
	* Subscriber topic
	* Publisher topic

Your node should be able to start (e.g. via `ros2 run`) even if not all of these parameters have been set.
If a parameter has not been set, your node should default to using the values given in the previous question.
This [link](https://roboticsbackend.com/rclpy-params-tutorial-get-set-ros2-params-with-python/) may be helpful.
This way of falling back to hard-coded defaults can still be useful, especially in cases where a sensible default for
a parameter is known and changes would only have to be made rarely.

Upload `fake_scan_publisher.py` to Gradescope.

### Question 8: Playing with Bag Files

In Question 3, we asked you to visualize your LaserScan data on RViz. The RViz visualization was probably meaningless and ugly because
you were publishing random data. Don't be alarmed; real LaserScan data is a lot prettier and more informative. Download these
[bagfiles](https://www.dropbox.com/scl/fi/z4ln37mh9twxmpzu7obx1/gmapping_data_active_only.zip?rlkey=nxiyhgfo2396acwxoztqbuo4k&dl=0), follow the
instructions [here](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html),
and visualize the LaserScan data on RViz. Try it with multiple coordinate frames.

> The provided bag files are from our cars driving around in the basement of Stata Center.

Recording your own bagfiles is also very important for reproducing test results and debugging your code.
Re-launch `my_first_launch.launch.xml` from Question 6, and run `ros2 topic list`. This is a useful command to see the list of
active topics. Now, while `my_first_launch.launch.xml` is launched, record a short (~4 seconds) rosbag named `my_first_bag` which
contains the topics `/fake_scan`, `/my_random_float`, and `/open_space`.

Once you've finished recording, stop `my_first_launch.launch.xml` and run `ros2 bag play my_first_bag -l`. The `-l` flag enables looping,
so the rosbag automatically restarts from the beginning when it reaches the end.

Open a new terminal and run `ros2 topic list`. You should see `/fake_scan`, `/my_random_float`, and `/open_space`
being published by the rosbag player.

Next, open another terminal and run your `simple_subscriber` node. You should observe that `/random_float_log` is now being published,
with the subscriber processing the `/my_random_float` data from the bagfile. This demonstrates how rosbags allow you to replay
identical input data for consistent debugging, testing, and evaluation.

Take a screenshot of **rqt_graph** showing:
- The `rosbag2_player` node publishing `/fake_scan`, `/my_random_float`, and `/open_space`
- Your `simple_subscriber` node running, subscribing to `/my_random_float`, and publishing to `/random_float_log`

Again, make sure to select `Nodes/Topics (all)` to display both nodes and topics, and uncheck `Hide Dead sinks` and `Hide Leaf topics`.
Upload the screenshot to Gradescope.

### Question 9: TF Exercises

In this question, we will use the `one_loop` bagfile from Question 8. Note that instead of `map`, this rosbag uses `odom`.

#### Part 1: The Hard Way

Begin by developing a ROS node that publishes the correct TF of the left and right cameras to the TF tree.
Name this node `dynamic_tf_cam_publisher.py`.

The left camera is located `0.05m` to the left of the `base_link` position, and the right camera is located `0.05m` to the right of
the `base_link` position. Both cameras have identity rotation relative to the `base_link` pose. In this case, the "forward" direction
is the positive-x axis, and the "left" direction is the positive-y axis.

Precompute the relative transforms between the cameras and `base_link` as 4x4 numpy arrays using the above information. Refer to
the lecture notes for the typical 4x4 formulation.

At each time step, your node should:

1. Get the current transform of the robot w.r.t. (with respect to) `odom`. Use the TF tree!
2. Convert the robot's transform to a 4x4 numpy array.
3. Compute the current transform of the left camera w.r.t. `odom` by composing the precomputed `base_link->camera` transform
    with the `odom->base_link` transform.
4. Compute the current transform of the right camera w.r.t **the left camera** by composing the relevant matrices.
5. Broadcast the computed transforms for the cameras to the TF tree. The left camera's TF should be broadcast on the
    `left_cam` frame, and the right camera's TF goes on `right_cam`.

Save a short (~4 seconds) video of RViz as the rosbag plays with your node running. Since this bagfile uses the `odom` frame, you
need to click the panel on the left and under global options, change `Fixed Frame: map` to `Fixed Frame: odom`. This changes the
"origin" of the RViz grid to the `odom` frame instead of the `map` frame (which doesn't exist in this bagfile). Additionally, make sure
we can see the `base_link` frame and both the left and right camera frames moving around by clicking `Add -> By display type -> TF`,
and make the camera follow `base_link` by changing `Target Frame: <Fixed Frame>` to `Target Frame: base_link` on the right panel.

Lastly, generate a PDF of your TF tree using `ros2 run tf2_tools view_frames`. Save and upload the video, PDF, and
`dynamic_tf_cam_publisher.py` to Gradescope. **Please submit the video as an MP4 or GIF!** Gradescope does not work
well with other video file formats.

* **Note 1:** Don't worry if the new TF frames are jittery and/or don't follow the `base_link` frame fast enough; this should be fixed in part 2.
* **Note 2:** You will be doing some transformations in your ROS node. You may find
    [SciPy](https://docs.scipy.org/doc/scipy/reference/spatial.transform.html#module-scipy.spatial.transform)
    spatial transforms to be useful.
* **Note 3:** Remember: your `left_cam` transform is defined relative to `odom`, and your `right_cam` transform is defined relative to
    `left_cam`. These require slightly different equations!

#### Part 2: The ~~Easy~~ Better Way

1. Write a ROS node that publishes the relative pose between each camera and the robot as a **static transform**. The static
    transforms to broadcast are `base_link->left_cam` and `left_cam->right_cam`. The node should only broadcast each transform
    once. Name this node `static_tf_cam_publisher.py`.
2. Write a ROS launch file that runs `static_tf_cam_publisher.py`. Name this launch file `static_tf_publisher.launch.xml`.

> Do NOT call `sendTransform` multiple times when broadcasting multiple static transforms. Instead, pass all of them as a list to a
> single `sendTransform` call.

Save a short (~4 seconds) video of RViz just as in part 1, but with your `static_tf_cam_publisher.py` node running. This should
look much smoother than in part 1. Upload the video and `static_tf_cam_publisher.py` to Gradescope. Again **please submit the video
as an MP4 or GIF!**

#### Part 3: Back to `base_link`

Write a new ROS node called `base_link_tf_pub.py`. This new node must listen to the transform between `left_cam` and `odom` and
then broadcast the transform from `odom` to `base_link` on a new frame: `base_link_2`. The transform you publish must be computed by
composing the transform between `left_cam` and `base_link` with the transform you are listening for. In other words, this **cannot**
be a static transform.

Add this node to your `static_tf_publisher.launch.xml` file, such that both the static transforms for the two cameras and
`base_link_2` are broadcasted when the launch file is executed. You should be able to visualize both `base_link` and `base_link_2`
on top of each other in RViz.

Save a short MP4 or GIF video of RViz again, and make sure you can see both `base_link_2` and `base_link` on top of each other.
Upload the video, `static_tf_publisher.launch.xml`, and `base_link_tf_pub.py` to Gradescope.

> **Hint:** Use `numpy.linalg.inv()`!

## Debugging Hints

Here are some helpful tools to use when trying to debug your code.

### `ros2 topic list`
Lists currently active topics which are being subscribed to, published to, or both.

### `ros2 node list`
Lists currently active nodes.

### `ros2 topic echo /topic_name`
Once you know that a command is being published/subscribed to, you can echo its contents, which can show whether or not any information is being passed across this topic or if you are not sending what you expect.

### `rqt_graph`
This is a tool to display graphs of running ROS nodes with connecting topics and package dependencies. Allows you to visualize your entire framework! 

### `rviz2`
This is a powerful 3D visualization tool for displaying sensor data and state information from ROS. You will be using it more extensively in future labs.

### `ros2 run rqt_plot rqt_plot`
This is a plotting tool that visualizes ROS2 topic data as a line graph, allowing you to see how values change over time.

### `ros2 run tf2_tools view_frames`
This creates a PDF file with a visualization of your TF tree.

To find more ways to use `ros2 topic`, type `ros2 topic --help` in the command line. There are many other helpful command line tools to
help you out too. See [here](https://docs.ros.org/en/humble/Concepts/About-Command-Line-Tools.html).
