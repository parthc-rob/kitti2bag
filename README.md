#Requirements :
=========================
0. Preferably Ubuntu system
1. ROS-Kinetic or above installed.
2. Python installed

##Steps 
0. Download kitti grayscale odometry dataset *and* ground truth poses from `http://www.cvlibs.net/datasets/kitti/eval_odometry.php`,
0.1 Organize the data in a directory structure as follows -

+-- kitti2bag/
   +-- dataset/
      +--poses/
      |  +-- _00.txt
      |  |
      |  +-- _01.txt ...
      +--sequences/
         +-- 00/
         |  +-- image_0 ...
         +-- 01/
	    ....

1. `sudo pip install --user pykitti`
2. `source /opt/ros/{distribution}/setup.bash` - for example: `source /opt/ros/kinetic/setup.bash` 
3.0 `chmod +x kitti2bag/kitti2bag.py`
3.1 `python kitti2bag/kitti2bag.py -s 00 odom_gray ./dataset/` - replace `00` with desired sequence. Our pipeline uses grayscale images.
4. Use `rosbag play kitti_data_odometry_gray_sequence_00.bag` to use this data for the DeepLCD and ORB SLAM2 parts of our repo. 
