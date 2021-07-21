# -7-29_Turtlebot3_setup-
## 概要
7/29　勉強会 turtlebot3のセットアップ用リポジトリ  
ros(melodic)がインストールされている前提でセットアップしていく
※ROSのセットアップをしていない場合はhttps://github.com/ryuichiueda/ros_setup_scripts_Ubuntu18.04_desktop からインストールしてください。  
## 目的
turtlebot3実機、もしくはシミュレーション環境をセットアップする
## 資料
ROBOTIS e-manual
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/
## 説明
資料にあるROBOTIS e-manualを参考にセットアップを行います。  
ubuntu18.04、ros_melodicがインストールされている前提でセットアップをしていきます。  
ROBOTIS e-manual　3.1.2 Instal ROS1 on Remort PCまでは飛ばし、
3.1.3 Install Dependent ROS 1 Packagesから進めていきます。  
※ubuntu18.04以外の場合、ubuntuのバージョンに対応するROSのバージョンに合わせてサイト上部のボタンをクリックしてください。実行するコマンド等がバージョンに合ったものに変更されます。
#### 図
![サイト上部にバージョンに合わせてセットアップ内容が変わるボタンがある](https://user-images.githubusercontent.com/72721963/126454556-23750bba-ec47-4e91-bf6f-d2b38288c0f3.png)
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
また、apt-getを使用してインストールしていますが、
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
