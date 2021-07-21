# -7-29_Turtlebot3_setup-
## 概要
7/29　勉強会 turtlebot3のセットアップ用リポジトリ  
ros(melodic)がインストールされている前提でセットアップしていく
## 目的
turtlebot3、そのシミュレーション環境をセットアップする
## 資料
ROBOTIS e-manual
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/
## 説明
資料にあるROBOTIS e-manualを参考にセットアップを行います。  
ubuntu18.04、ros_melodicがインストールされている前提でセットアップをしていきます。  
サイトの3.1.2 Instal ROS1 on Remort PCまでは飛ばし、
3.1.3 Install Dependent ROS 1 Packagesから進めていきます。  
※ubuntu18.04以外の場合、バージョンに合わせてサイト上部のボタンをクリックしてください。
### 図
![サイト上部にバージョンに合わせてセットアップ内容が変わるボタンがある](https://user-images.githubusercontent.com/72721963/126454556-23750bba-ec47-4e91-bf6f-d2b38288c0f3.png)
3.1.3 Install Dependent ROS 1 Packages では
```
apt-get
```
になっていますが、
```
apt
```
でも問題ないはずです。
