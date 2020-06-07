# Dolly the robot

_It's a sheep, it's a dolly, it's a following robot. Dolly was born to be cloned._

Packages for launching Dolly demo, which uses Gazebo and ROS 2.

![Dolly city](dolly.gif)

## Versions

Dolly has been tested on:

* ROS 2 version:
    * ROS Crystal: `crystal` branch
    * ROS Dashing: `dashing` branch
    * ROS Eloquent: `master` branch
* Gazebo version:
    * Gazebo 9
* Operating system:
    * Ubuntu Bionic
    * OSX Sierra (thanks, @Karsten1987 !)

## Install

Install instructions for Ubuntu Bionic.

1. Install the appropriate ROS 2 version as instructed [here](https://index.ros.org/doc/ros2/Installation/Linux-Install-Debians/).

1. Clone Dolly:

        mkdir -p ~/ws/src
        cd ~/ws/src
        git clone https://github.com/chapulina/dolly

1. Install dependencies:

        cd ~/ws
        rosdep install --from-paths src --ignore-src -r -y

1. Build and install:

        cd ~/ws
        colcon build

## Run

1. Setup environment variables (the order is important):

        . /usr/share/gazebo/setup.sh
        . ~/ws/install/setup.bash

1. Launch Dolly in a city (this will take some time to download models):

        ros2 launch dolly_gazebo dolly.launch.py

1. Launch Dolly in an empty world:

        ros2 launch dolly_gazebo dolly.launch.py world:=empty.world

## Packages

This repository contains the following packages:

* `dolly`: Metapackage which provides all other packages.
* `dolly_follow`: Simulation-agnostic code that generates velocity commands
                  based on laser sensor readings.
* `dolly_common`: Helpers for running simulation. It's simulator-agnostic.
* `dolly_gazebo`: Launch Dolly in a Gazebo simulation.

# TODO

* Make Dolly's model available to RViz

