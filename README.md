# -7-29_Turtlebot3_setup-
## 概要
7/29　勉強会 turtlebot3のセットアップ用リポジトリ  
ROS(melodic)がインストールされている前提でセットアップしていく  
※ROSのセットアップをしていない場合は、https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu18.04_desktop からインストールしてください。

## 目的
turtlebot3実機、もしくはシミュレーション環境をセットアップする

## 資料
ROBOTIS e-manual
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/

## 説明
資料にあるROBOTIS e-manualを参考にセットアップを行います。  
ROBOTIS e-manual　3. Quick Start Guide の 3.1 PC Setup から始めていきます。
また、今回はubuntu18.04、ROS(melodic)がインストールされている前提でセットアップをしていきます。  
ROBOTIS e-manual　3.1.2 Instal ROS1 on Remort PCまでは飛ばし、
3.1.3 Install Dependent ROS 1 Packagesから進めていきます。  
※ubuntu18.04以外の場合、ubuntuのバージョンに対応するROSのバージョンに合わせてサイト上部のボタンをクリックしてください。実行するコマンド等がバージョンに合ったものに変更されます。
#### 図
![7-29-勉強会スクショ１](https://user-images.githubusercontent.com/72721963/127088537-66f0143e-b82e-4e1b-be79-36cd6a96ec64.png)

### ワークスペース(workspace)の作成
必要なパッケージをダウンロードする前に、ワークスペースを作ります。

```
$ mkdir -p catkin_ws/src
$ cd ~/catkin_ws/src
```
今回のワークスペースの名前は、catkin_wsとして、
catkin_wsの中に、srcというディレクトリを作ります。
このsrcの中に、必要なパッケージ等をダウンロードしていきます。

### 3.1.3 Install Dependent ROS 1 Packages
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

### 6.1
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_mak
```
