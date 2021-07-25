
Set locale

Make sure you have a locale which supports UTF-8. If you are in a minimal environment (such as a docker container), the locale may be something minimal like POSIX. We test with the following settings. However, it should be fine if you’re using a different UTF-8 supported locale.

locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings

Setup Sources

You will need to add the ROS 2 apt repositories to your system. To do so, first authorize our GPG key with apt like this:

sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

And then add the repository to your sources list:

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

Install ROS 2 packages

Update your apt repository caches after setting up the repositories.

sudo apt update

Desktop Install (Recommended): ROS, RViz, demos, tutorials.

sudo apt install ros-foxy-desktop

ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.

sudo apt install ros-foxy-ros-base

Environment setup
Sourcing the setup script

Set up your environment by sourcing the following file.

source /opt/ros/foxy/setup.bash

lets Try some examples

If you installed ros-foxy-desktop above you can try some examples.

In one terminal, source the setup file and then run a C++ talker:

source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_cpp talker

In another terminal source the setup file and then run a Python listener:

source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_py listener

You should see the talker saying that it’s Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly. Hooray!
Next steps after installing

Continue with the tutorials and demos to configure your environment, create your own workspace and packages, and learn ROS 2 core concepts.
Using the ROS 1 bridge

The ROS 1 bridge can connect topics from ROS 1 to ROS 2 and vice-versa. See the dedicated documentation on how to build and use the ROS 1 bridge.
Additional RMW implementations (optional)

The default middleware that ROS 2 uses is Fast-RTPS, but the middleware (RMW) can be replaced at runtime. See the guide on how to work with multiple RMWs.
Troubleshooting

Troubleshooting techniques can be found here.
Uninstall

If you need to uninstall ROS 2 or switch to a source-based install once you have already installed from binaries, run the following command:

sudo apt remove ros-foxy-* && sudo apt autoremove


