# M3500-pose-graph
Acquire Manhattan 3500 Optimized Pose Graph

## Requirements
### Install ceres-solver
```
git clone https://ceres-solver.googlesource.com/ceres-solver
sudo apt-get install cmake
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libatlas-base-dev
sudo apt-get install libeigen3-dev
sudo apt-get install libsuitesparse-dev
```
Now, we can Build, test, and install ceres-solver
```
wget http://ceres-solver.org/ceres-solver-2.0.0.tar.gz
tar zxf ceres-solver-2.0.0.tar.gz
mkdir ceres-bin
cd ceres-bin
cmake ../ceres-solver-2.0.0
make -j3
make test
make install
```
* Try this if encounter 'boost' error:
```sudo apt-get install libboost-dev```

### Install Eigen3
Completed when install g2opy

## How to compile
### Compile
```
mkdir build
cd build
cmake ..
make
```
### Run Executable
```
./toy_pose_graph
```

This executable reads file `../input_M3500_g2o.g2o` and produces
`../init_nodes.txt`, `../init_edges.txt`
`../after_opt_nodes.txt`, `../after_opt_edges.txt` and `../switches.txt`

### Visualize Results
We have provided a python script to visualize the results. The text files to supply should contain lines as : `id x y theta` representing every node.

```
cd .. #come out of build directory
python plot_results.py --initial_poses init_nodes.txt --optimized_poses after_opt_nodes.txt
```
