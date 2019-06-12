# Examples

## Building notes

OpenCL examples:

- To enable the building of OpenCL examples, configure Etaler using:
```shell
cd Etaler
mkdir build
cd build
cmake -DETALER_ENABLE_OPENCL=TRUE ..
make
```

MKL-DNN example:

- The following bash commands can be used to build [MKL-DNN](https://github.com/intel/mkl-dnn) from source:
```shell
git clone https://github.com/intel/mkl-dnn.git
cd mkl-dnn
mkdir build
cd build
cmake -DMKLDNN_USE_MKL=NONE -DMKLDNN_THREADING=OMP:COMP ..
make
sudo make install
```

- The MKL-DNN example can then be enabled in Etaler using:
```shell
cd Etaler
mkdir build
cd build
cmake -DETALER_MKL_DNN_EXAMPLE=TRUE ..
make
```
