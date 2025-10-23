## ORB_SLAM3 Intallation

First, install dependencies:
```
sudo apt update
sudo apt install -y build-essential cmake git libgtk-3-dev \
    pkg-config libavcodec-dev libavformat-dev libswscale-dev \
    libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev \
    libdc1394-22-dev libopenexr-dev libwebp-dev \
    python3-dev python3-numpy
sudo apt install -y libeigen3-dev
```

Pangolin:
```
cd ~
git clone https://github.com/stevenlovegrove/Pangolin.git
cd Pangolin
mkdir build && cd build
cmake ..
cmake --build .
sudo make install
```

Add those lines to .bashrc:
```
export CMAKE_PREFIX_PATH=$CMAKE_PREFIX_PATH:/usr/local
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
```

Install ORB_SLAM3:
```
cd ~
git clone https://github.com/UZ-SLAMLab/ORB_SLAM3.git
```

IMPORTANT NOTE: Before building ORB-SLAM3 make sure your OpenCV version is 4.5.4 with 
```
pkg-config --modversion opencv4
```

Build:
```
cd ORB_SLAM3
chmod +x build.sh
./build.sh
```


### Test the installation

First we need a dataset to test the installation download it with:

```
cd ORB_SLAM3/Examples/Monocular
wget https://vision.in.tum.de/rgbd/dataset/freiburg1/rgbd_dataset_freiburg1_xyz.tgz
tar -xvzf rgbd_dataset_freiburg1_xyz.tgz
```

Run ORB-SLAM3 with this dataset:
```
./mono_tum ../../Vocabulary/ORBvoc.txt ../../Examples/Monocular/TUM1.yaml ./rgbd_dataset_freiburg1_xyz

```
