MotionSensorExample
===================

Fork别人的代码，以下英文是原版的README。
笔者试用了下，在Pi2上编译出错，原因是结构体的初始化问题，Pi2的g++版本似乎不支持结构体的复合字面量初始化方式。
因此笔者修改了初始化的代码，试着编译了用于MPU6050的测试代码，通过了，如下图所示。经验证也确实可以拿到roll、pitch、yaw数据（DMP方式）。
不过如果选择编译用于MPU9250的版本，却不能完成MPU的初始化。这个后面有空再定位修改。
还好的是，可以把MPU9250当MPU6050用（笔者也正是用MPU9250测试的）。

![](https://github.com/uname/MotionSensorExample/blob/master/snapshot.png)

MPU6050/MPU6500/MPU9150/MPU9250 over I2c for RaspberryPi using official Invensense libraries (v5.1):
http://www.invensense.com/developers/index.php?_r=downloads


This is a sample program for testing your MPU Motion Sensor with Rasperry Pi.
It does all the initialization and gathers:
- gyro
- accel
- quaternion
- compass (for MPU9XXX)
- temperature

and calculates Yaw, Pitch, Roll in degrees which in turn is displayed as an output.


**Wiring**
I2C uses only2 wires for data transmission: SCL and SDA
RPi pin 3 -> MPU SDA
RPi pin 5 -> MPU SCL


You will also need to provide power (3.3V) to your MPU. You can use external power or hook it up with RPi.
For example:
RPi pin 1 (3.3V) -> MPU VCC
RPi pin 6 (Ground) -> MPU GND


**Compilation:**
On RPi, edit MotionSensor/Makefile and adjust CXX_OPTS to specify your board (-DMPU6050 for MPU6050, -DMPU9150 for MPU9150), issue make


**Cross compiling:**
Edit all Makefiles in all directories and adjust CXX. Issue make


**Running:**
  make sure you have i2c_dev module loaded (modprobe i2c_dev)
  run mstest
  
*Output:*
Initializing I2C devices...
Testing device connections...
MPU6050 connection successful
Initializing DMP...
Enabling DMP...
DMP ready!
Initializing IMU...
Checking... Done.
IMU init done; offset values are :
yaw = -0.169205, pitch = -1.301078, roll = -1.168776

yaw = -0.174            pitch = 1.325           roll = -1.219   t = 20.24       1       0       0
yaw = -0.179            pitch = 1.350           roll = -1.267   t = 20.22       2       0       0
yaw = -0.185            pitch = 1.372           roll = -1.314   t = 20.23       3       0       0
yaw = -0.190            pitch = 1.395           roll = -1.361   t = 20.21       4       0       0
yaw = -0.195            pitch = 1.418           roll = -1.410   t = 20.23       5       0       0
yaw = -0.201            pitch = 1.441           roll = -1.454   t = 20.23       6       0       0
yaw = -0.206            pitch = 1.465           roll = -1.498   t = 20.23       7       0       0
yaw = -0.211            pitch = 1.485           roll = -1.545   t = 20.23       8       0       0
yaw = -0.216            pitch = 1.506           roll = -1.587   t = 20.23       9       0       0

....

**Additional info:**
Current setup is to run at 40Hz, this can be adjusted in the ms_open function, however note that your code will need to read the values with respective speed or quicker. Otherwise the MPU fifo buffer will overflown.

To read MPU see ms_update - it calls 'dmp read fifo' in a while loop. This means that if fifo is empty this will stall until a packet is available.

-------------------------
Gregory Dymarek
