OpenWrt repository for mpu6050
========
Binaries built from this repository on 2016-08-02 can be downloaded from http://leon0516.github.io/openwrt-mpu6050-example/.
To install the mpu6050 package, run
```
echo "src/gz announce http://leon0516.github.io/mpu6050" >> /etc/opkg.conf
opkg update
opkg install mpu6050
```
