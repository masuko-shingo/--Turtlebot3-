# -7-29_Turtlebot3_setup-
## 概要
7/29　勉強会 turtlebot3のセットアップ用リポジトリ  
ubuntu18.04 ,ROS(melodic)がインストールされている前提でセットアップしていく  
※ROSのセットアップをしていない場合は、https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu18.04_desktop からインストールしてください。

## 目的
turtlebot3シミュレーション環境をセットアップする

## 資料
ROBOTIS e-manual PCsetup  
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/  
ROBOTIS e-manual simulation  
https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/  

## 説明
資料にあるROBOTIS e-manualを参考にセットアップを行います。  
ROBOTIS e-manual　3. Quick Start Guide の 3.1 PC Setup から始めていきます。
また、今回はubuntu18.04、ROS(melodic)がインストールされている前提でセットアップをしていきます。  
ROBOTIS e-manual　3.1.2 Instal ROS1 on Remort PCまでは飛ばし、
3.1.3 Install Dependent ROS 1 Packagesから進めていきます。  
※ubuntu18.04以外の場合、ubuntuのバージョンに対応するROSのバージョンに合わせてサイト上部のボタンをクリックしてください。実行するコマンド等がバージョンに合ったものに変更されます。
#### バージョン変更のボタンの参考
![7-29-勉強会スクショ１](https://user-images.githubusercontent.com/72721963/127088537-66f0143e-b82e-4e1b-be79-36cd6a96ec64.png)


### 3.1.3 Install Dependent ROS 1 Packages
ここでは、turtlebot3を動かすために必要な依存パッケージをインストールします。
3.1.3 Install Dependent ROS 1 Packagesでは
```
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
```
とコマンドが記述されていますが、この方法でうまくインストールできない場合
```
$ sudo apt-get install ros-melodic-joy 
$ sudo apt-get install ros-melodic-teleop-twist-joy
...
```
のように一つずつインストールを行ってください。  
また、ROBOTIS e-manualでは基本的にapt-getを使用してインストールしていますが、
```
$ sudo apt install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
```

```
$ sudo apt install ros-melodic-joy 
$ sudo apt install ros-melodic-teleop-twist-joy
...
```
のようにaptでインストールしても問題ありません。
### 3.1.4 Install TurtleBot3 Packages
```
$ sudo apt install ros-melodic-dynamixel-sdk
$ sudo apt install ros-melodic-turtlebot3-msgs
$ sudo apt install ros-melodic-turtlebot3
```
### 3.1.5 Set TurtleBot3 Model Name
ここでは、用いるturtlebot3のモデルを設定していきます。  
turtlebot3には、  
* burger  
* waffle  
などいくつかありますが、今回はburgerを使います。
```
$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```

### ワークスペース(workspace)の作成
必要なパッケージをダウンロードする前に、ワークスペースを作ります。

```
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
```
今回のワークスペースの名前は、catkin_wsとして、
catkin_wsの中に、srcというディレクトリを作ります。　　
このcatkin_ws/srcの中に、必要なパッケージ等をダウンロードしていきます。

### 6.1 Gazebo Simulation
ここでは、GazeboというROSのパッケージを使ってシミュレーションを行います。
ここからは、資料にある  
ROBOTIS e-manual simulation  
https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/  
を参考にしてみてください。

### 6.1.1 Install Simulation Package
シミュレーションに必要なパッケージ、gmappingに必要なパッケージをインストールします。
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_gazebo_plugin.git
$ git clone https://github.com/ros-perception/slam_gmapping.git
$ git clone https://github.com/ros-perception/openslam_gmapping.git
$ git clone https://github.com/ros-planning/navigation_msgs.git
$ git clone https://github.com/ros-planning/navigation.git
$ git clone https://github.com/ros/geometry2.git
$ cd ~/catkin_ws && catkin_make
```
catkin_ws/srcに移動し、turtlebot3のシミュレーション環境を-bでブランチを指定して、git cloneで自分の環境に複製します。  
git clone後は、catkin_wsに移動し、catkin_makeというコマンドでビルドしていきます。

### 6.1.2 Launch Simulation World
インストール、ビルドができたら  
gazeboでシミュレータを立ち上げてみます。
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
gazeboが立ち上がり、亀のようなワールドとturtlebot3がいれば完了です。  
ctrl+alt+tで新しく端末を開いて、teleop_keyを実行すればシミュレータ内のturtlebot3を動かすことができます。
```
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch 
```
#### 立ち上がった際の図
![8月5日勉強会turltebot3simulatorスクショ](https://user-images.githubusercontent.com/72721963/128228635-71c8154f-1397-481a-9cd9-0f45970cf3cf.png)

### gazeboを実行した際に、このようなエラーが出る場合
```
$ gazebo worlds/turtlebot3_burger.world
[Err] [REST.cc:205] Error in REST request

libcurl: (51) SSL: no alternative certificate subject name matches target host name 'api.ignitionfuel.org'
```
~/.ignition/fuelにある、config.yamlファイルの一部を変更してください。
```
$ cd ~/.ignition/fuel
$ ls
config.yaml
```
~/.ignition/fuelまで移動、configファイルがあるか確認  
#### configファイルの一部行を変更  
```
url: https://api.ignitionfuel.org
```
から、
```
url: https://api.ignitionrobotics.org
```
に変更する。  
任意のエディタで変更(今回はvim)
```
$ vim config.yaml 
```
変更できたか確認
```
$ cat config.yaml 
---
# The list of servers.
servers:
  -
    name: osrf
    url: https://api.ignitionrobotics.org

  # -
    # name: another_server
    # url: https://myserver

# Where are the assets stored in disk.
# cache:
#   path: /tmp/ignition/fuel
```
この変更を行った後、再度gazeboを立ち上げ、エラーが出なければ成功です。
