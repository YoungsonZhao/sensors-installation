# Instructions for Sensors Installation
The operation system is Ubuntu 16.04 and the ROS version is Kinetic.
## Kinect Xbox One
* Download libfreenect2 source
    ```
    git clone https://github.com/OpenKinect/libfreenect2.git
    cd libfreenect2
    ```
* Install build tools
    ```
    sudo apt-get install build-essential cmake pkg-config
    ```
* Install libusb. The version must be >= 1.0.20.
    ```
    sudo apt-get install libusb-1.0-0-dev
    ```
* Install TurboJPEG
    ```
    sudo apt-get install libturbojpeg libjpeg-turbo8-dev
    ```
* Install OpenGL
    ```
    sudo apt-get install libglfw3-dev
    ```
* Install OpenNI2 (optional)
    ```
    sudo apt-get install libopenni2-dev
    ```
* Build
    ```
    mkdir build && cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2
    make
    make install
    ```
    You need to specify `cmake -Dfreenect2_DIR=$HOME/freenect2/lib/cmake/freenect2` for CMake based third-party application to find libfreenect2.
* Set up udev rules for device access
    ```
    sudo cp ../platform/linux/udev/90-kinect2.rules /etc/udev/rules.d/
    ```
* Replug the Kinect and Run the test program
    ```
    ./bin/Protonect
    ```
