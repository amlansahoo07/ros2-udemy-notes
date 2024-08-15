# ROS2-Course-Notes

## ROS2 Introduction

ROS2 (Robot Operating System 2) is an open-source framework for developing robot software. It builds on the original ROS (Robot Operating System) but introduces several new features, improvements, and optimizations designed to meet the needs of modern robotics. 

ROS2 is designed to support complex, distributed robotic systems, making it easier to develop, deploy, and manage the various software components that control robots. It provides tools and libraries for building, simulating, and testing robotic systems, and it is widely adopted in both academic research and industrial applications.

### Key Features of ROS2:
- **Cross-Platform Support**: ROS2 supports multiple operating systems, including Linux, Windows, and macOS.
- **Real-Time Capability**: With a focus on real-time performance, ROS2 can handle time-critical tasks, making it suitable for applications like autonomous vehicles and industrial automation.
- **Security**: ROS2 introduces security features like encrypted communication, ensuring the integrity and confidentiality of data between nodes.
- **Scalability**: Designed to work on everything from microcontrollers to large-scale cloud deployments, ROS2 can scale with your project requirements.
- **Modular Design**: ROS2's modular architecture allows for easy integration and substitution of components, promoting code reuse and flexibility.

## Why ROS2?

### 1. Code Separation and Communication Tools
ROS2 provides a clear separation between different components of a robotic system. This modularity allows for easier development, testing, and maintenance of each part. 

- **Nodes**: ROS2 uses nodes to represent independent processes that perform specific tasks. These nodes can communicate with each other using various communication tools like topics, services, and actions.
- **Topics**: Topics are used for asynchronous communication between nodes. Nodes can publish data to a topic or subscribe to it to receive data. This decoupling of data producers and consumers simplifies the overall architecture.
- **Services and Actions**: ROS2 also supports synchronous communication through services, where a node can request data or trigger actions in another node. Actions extend this concept to long-running tasks, allowing nodes to send feedback and results over time.

This separation and the robust communication tools provided by ROS2 make it easier to build scalable and maintainable robotic systems.

### 2. Tools and Plug n Play Libraries
ROS2 comes with a rich set of tools and libraries that significantly speed up development. These tools are designed to be modular, allowing you to easily plug and play different components.

- **RViz**: A 3D visualization tool that helps in visualizing sensor data, robot state, and more.
- **Gazebo**: A simulation environment that allows you to test your algorithms in a virtual world before deploying them to real robots.
- **ROS2 Libraries**: ROS2 provides a wide range of libraries for tasks like motion planning, perception, and control. These libraries are often community-driven and well-maintained, offering tested solutions to common problems.

The plug-and-play nature of these tools and libraries means you can quickly integrate them into your projects, saving time and effort.

### 3. Language Agnosticism
One of the significant advantages of ROS2 is its language agnosticism. ROS2 supports multiple programming languages, including C++, Python, and more.

- **C++ and Python**: While C++ is often used for performance-critical components, Python is widely used for rapid prototyping and scripting. The ability to use both languages interchangeably within the same ROS2 system provides flexibility in development.
- **Other Languages**: ROS2 also supports other languages like JavaScript, Lua, and more, thanks to its robust client libraries and community-driven efforts.

This language agnosticism allows developers to choose the best language for each part of their system, enabling a more tailored and efficient development process.

## Installation and Environment Setup

### 1. Installation on Ubuntu

To install ROS2 on Ubuntu, follow the official installation guide for the ROS2 Humble distribution:

[ROS2 Humble Installation on Ubuntu](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)

This guide provides detailed instructions on setting up the required repositories, installing the necessary packages, and verifying your installation.

### 2. Environment Setup

Once ROS2 is installed, you need to configure your environment to use ROS2 tools and libraries effectively.

#### Sourcing ROS2 Setup File

After installation, you must source the `setup.bash` file from the global ROS2 installation folder. This sets up your environment variables, including paths to ROS2 executables and libraries.

```bash
source /opt/ros/humble/setup.bash
```

This command is necessary each time you open a new terminal window to use ROS2.

#### Why and Which Files to Source

Sourcing the `setup.bash` file is crucial because it configures your shell to recognize ROS2 commands like `ros2`, `colcon`, and others. Depending on your setup, you might need to source additional setup files, such as those for your workspace or specific packages:

- **Global Installation**: `/opt/ros/humble/setup.bash`
- **Workspace Setup**: If you're working in a custom ROS2 workspace, you should also source the `setup.bash` from that workspace:
 ```bash
 source ~/ros2_ws/install/setup.bash
 ```

By sourcing these files, you're ensuring that all necessary paths and environment variables are correctly configured, enabling smooth development and execution of ROS2 applications.

#### Prevent Repetition by Adding to `.bashrc`

To avoid manually sourcing the setup files every time you open a new terminal, you can add the sourcing command to your `.bashrc` file. This ensures that the setup is automatically loaded each time you start a new terminal session.

Open your `.bashrc` file with a text editor:

```bash
nano ~/.bashrc
```

Add the following line to the end of the file:

```bash
source /opt/ros/humble/setup.bash
```

If you're using a workspace, also add:

```bash
source ~/ros2_ws/install/setup.bash
```

Save and close the file, then source the `.bashrc` to apply the changes:

```bash
source ~/.bashrc
```

### 3. Demo: Listener and Talker Code

To ensure that your ROS2 installation and environment setup are working correctly, you can run a simple demo using the ROS2 "listener" and "talker" nodes.

#### Listener Node

First, open a new terminal and run the listener node:

```bash
ros2 run demo_nodes_cpp listener
```

This node will subscribe to a topic and print out messages it receives.

#### Talker Node

In another terminal, run the talker node:

```bash
ros2 run demo_nodes_cpp talker
```

This node will publish messages to a topic that the listener is subscribed to.

If everything is set up correctly, you should see the listener terminal printing out the messages sent by the talker node. This confirms that your ROS2 installation and environment setup are working as expected.

