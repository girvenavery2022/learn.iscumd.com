
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




