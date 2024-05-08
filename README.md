
- You can see the original version from [ldrobot](https://github.com/ldrobotSensorTeam/ldlidar_stl_sdk), here is a detailed usage guideline:

# First step: Setup driver for your device
(The driver works only for product by Ldrobot, LD06/LD19 )
So make sure your device is this two type:
> - LDROBOT LiDAR LD06
> - LDROBOT LiDAR LD19
### Always remember `cd` to your workspace

## 0. Create your workspace and get the driver from GitHub Repo within your workspace:
```bash
cd ~

mkdir  ldlidar_ws

cd ldlidar_ws

git clone  https://github.com/ldrobotSensorTeam/ldlidar_stl_sdk.git
```

## 1. Before compiling: make sure you installed CMake and g++
```bash
sudo apt-get update
sudo apt-get install cmake
sudo apt-get install g++
```

## 2. Check the location of your radar
`ls -l /dev` or `sudo dmesg | grep tty`

## 3. Give permission for the serial port device — change the path to your own radar
```bash
sudo chmod 777 /dev/ttyUSB0
```

Well, I assume you connected the LiDAR to your system motherboard via an onboard serial port or usB-to-serial module (for example, CP2102 module).

## 4. Give permission to .sh file, and run the build file
```bash
cd ~/ldlidar_ws/ldlidar_stl_sdk

chmod +x auto_build.sh
./auto_build.sh
```

## 5. Give permission to  ./start_node.sh and run it
```bash
chmod +x start_node.sh
./start_node.sh
```

## Finally it will work
Then during the process, you need to input the value of your own device(This is just an example of mine): 

> `input [product_type]=LD19`  
> `input [communication_mode]=serial`  
> `input [serial_port_number]=/dev/ttyUSB0`  # Change it into the path of your lidar  
> `input [server_ip]=xxx.xx.x.xxx`  
> `input [server_port]=2024`  # Any number just not the same with currently using port



Check the serial port number of lidar:
```bash
sudo dmesg | grep tty
```
Find the server ip:
```bash
ip addr
```
