# openwrt-mpu6050-example

[![Build Status](https://travis-ci.org/leon0516/openwrt-mpu6050-example.svg?branch=master)](https://travis-ci.org/leon0516/openwrt-mpu6050-example)

mpu6050应用程序基于OpenWrt平台。  
OpenWrt需开启I2C特性  
有可能需要编辑dts文件(本人使用的WrtNode板子，需要编辑)

依赖：libstdcpp

本项目基于Travis CI 持续自动编译。可以到[releases](https://github.com/leon0516/openwrt-mpu6050-example/releases)下载ipk包  

运行log
```
root@OpenWrt:~# mpu6050
Initializing MPU...
Setting MPU sensors...
Setting GYRO sensitivity...
Setting ACCEL sensitivity...
Powering up MPU...
MPU6050 connection successful
Setting MPU fifo...
Loading DMP firmware...
Activating DMP...
Configuring DMP...
Setting DMP fifo rate...
Resetting fifo queue...
Checking... Done.
yaw = -0.5	pitch = 0.4	roll = -8.3	temperature = 32.5	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.5	roll = -8.7	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.5	roll = -9.0	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.5	roll = -9.4	temperature = 32.5	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.5	roll = -9.8	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.5	roll = -10.2	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.6	pitch = 0.6	roll = -10.6	temperature = 32.5	compass = 0.0, 0.0, 0.0
yaw = -0.7	pitch = 0.6	roll = -11.0	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.7	pitch = 0.6	roll = -11.5	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.7	pitch = 0.6	roll = -11.9	temperature = 32.4	compass = 0.0, 0.0, 0.0
yaw = -0.7	pitch = 0.6	roll = -12.3	temperature = 32.5	compass = 0.0, 0.0, 0.0
```
