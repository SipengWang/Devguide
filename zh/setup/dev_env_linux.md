# Linux环境下的开发

Linux允许您构建[所有PX4目标](../setup/dev_env.md#supported-targets)(基于NuttX的硬件、高通骁龙飞行硬件、基于Linux的硬件、仿真、ROS)。

> **TIP** [Ubuntu Linux LTS](https://wiki.ubuntu.com/LTS) 16.04是对于大部分开发的测试/支持Linux环境。 带有ROS Melodic的Ubuntu 18.04 LTS用于 [ROS开发](#ros). 同时提供来关于[CentOS](../setup/dev_env_linux_centos.md) and [Arch Linux](../setup/dev_env_linux_arch.md)的说明。

下文说明了如何使用方便的bash脚本在Ubuntu LTS上设置开发环境。 有关*手动安装*和其他目标的说明, 可参见[Ubuntu/Debian Linux](../setup/dev_env_linux_ubuntu.md)。

## 开发工具链

下面说明了如何使用[bash脚本](../setup/dev_env_linux_ubuntu.md#convenience-bash-scripts)在Ubuntu上设置开发工具链。 以下脚本作用分别是安装*Qt Creator IDE*、[ Ninja构建系统](https://ninja-build.org/)、[通用依赖项](../setup/dev_env_linux_ubuntu.md#common-dependencies)、[FastRTPS](../setup/dev_env_linux_ubuntu.md#fastrtps-installation), 以及将PX4源下载到您的目录(**~/src/Firmware**)。

> **Tip** 这些脚本已经在纯净版的 Ubuntu LTS 16.04和Ubuntu LTS 18.04安装系统上通过了测试。如果安装在除上述提到的系统或其他Ubuntu版本上, 则它们*可能*无法正常工作。 如果您遇到任何问题, 请参照[手动安装说明](../setup/dev_env_linux_ubuntu.md)操作。

首先使得电脑账户进入群组"dialout":

1. 在命令提示符下输入: 
        sh
        sudo usermod -a -G dialout $USER

2. 注销并重新登录(更改后重新登录生效)。

请对应以下各部分中的开发目标说明进行操作。

### Pixhawk/NuttX（和jMAVSim）

安装开发工具链:

1. 下载<a href="https://raw.githubusercontent.com/PX4/Devguide/{{ book.px4_version }}/build_scripts/ubuntu_sim_nuttx.sh" target="_blank" download>ubuntu_sim_nuttx.sh</a>.
2. 在bash shell中运行脚本: 
        bash
        source ubuntu_sim_nuttx.sh 随着脚本的运行，可能需要确认一些提示。

3. 完成后重新启动计算机。

### 高通骁龙飞控

在*PX4用户指南*中提供了高通骁龙飞控的安装说明:

* [开发环境](https://docs.px4.io/en/flight_controller/snapdragon_flight_dev_environment_installation.html)
* [软件安装](https://docs.px4.io/en/flight_controller/snapdragon_flight_software_installation.html)
* [配置](https://docs.px4.io/en/flight_controller/snapdragon_flight_configuration.html)

### 树莓派

安装开发工具链:

1. 下载<a href="https://raw.githubusercontent.com/PX4/Devguide/{{ book.px4_version }}/build_scripts/ubuntu_sim_common_deps.sh" target="_blank" download>ubuntu_sim_common_deps.sh</a> (这个文件中包含jMAVSim模拟器以及常用的工具链依赖环境)。
2. 在 bash shell 中运行脚本: 
        bash
        source ubuntu_sim_common_deps.sh 随着脚本的运行，可能需要确认一些提示。

3. 按照[树莓Pi](../setup/dev_env_linux_ubuntu.md#raspberry-pi-hardware)在[Ubuntu/Debian Linux](../setup/dev_env_linux_ubuntu.md)中的安装说明进行。

### Parrot Bepop

请按照此处的(手动)说明操作: [ Ubuntu/Debian Linux >Parrot Bebop](../setup/dev_env_linux_ubuntu.md#raspberry-pi-hardware)。

### jMAVSim/Gazebo 模拟

为了安装Gazebo9和jMAVSim模拟器：

1. 下载<a href="https://raw.githubusercontent.com/PX4/Devguide/{{ book.px4_version }}/build_scripts/ubuntu_sim.sh" target="_blank" download>ubuntu_sim.sh</a>.
2. 在bash shell中运行脚本: 
        bash 
        source ubuntu_sim.sh 随着脚本的运行，可能需要确认一些提示。

> **TIP** 如果你只需要jMAVSim模拟器，下载并运行<a href="https://raw.githubusercontent.com/PX4/Devguide/{{ book.px4_version }}/build_scripts/ubuntu_sim_common_deps.sh" target="_blank" download>ubuntu_sim_common_deps.sh</a>即可。

<span><span></p> 

<blockquote>
  <p>
    <strong>Note</strong> PX4兼容Gazebo7、8和9。 The script installs Gazebo 9.
  </p>
</blockquote>

<h3 id="ros">
  Gazebo with ROS Melodic
</h3>

<blockquote>
  <p>
    <strong>Note</strong> PX4 is tested with ROS Melodic on Ubuntu 18.04 LTS. ROS Melodic does not work on Ubuntu 16.04.
  </p>
</blockquote>

<p>
  下载开发环境工具链：
</p>

<ol start="1">
  <li>
    下载<a href="https://raw.githubusercontent.com/PX4/Devguide/{{ book.px4_version }}/build_scripts/ubuntu_sim_ros_melodic.sh" target="_blank" download>ubuntu_sim_ros_melodic.sh</a>。
  </li>
  
  <li>
    在命令行中运行脚本: <pre><code>bash
source ubuntu_sim_ros_melodic.sh</code></pre> 在脚本运行的时候你可能需要同意一些提示。
  </li>
</ol>

<p>
  Note:
</p>

<ul>
  <li>
    ROS Melodic默认使用Gazebo9安装
  </li>
  <li>
    你的catkin (ROS构建系统)工作空间位于<strong>~/catkin_ws/</strong>。
  </li>
</ul>

<h2>
  其他工具
</h2>

<p>
  运行/模拟工具链安装结束之后，参考<a href="../setup/generic_dev_tools.md">其他工具</a>来获取关于其他有用的工具的信息。
</p>

<h2>
  下一步
</h2>

<p>
  一旦你完成了环境的搭建，继续参考<a href="../setup/building_px4.md">运行建议</a>进行下一步工作。
</p>
