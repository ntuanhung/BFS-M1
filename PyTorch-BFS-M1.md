# PyTorch Build-From-Source for Apple Silicon
**NOTE**: This document is useful only for **scratch build** from PyTorch source code for Apple Silicon (or M1 chips such as M1, M1 Pro, M1 Max).

## References
- Blog: https://www.hendrik-erz.de/post/setting-up-python-numpy-and-pytorch-natively-on-apple-m1
- GitHub Issue: https://github.com/pytorch/pytorch/issues/48145

## Work-flow
- install prerequisites
- download pytorch source from repository
- install pytorch through a wheel-build


## Test Environment @2022/03/01
- Macbook Pro 14inch, 2021 with Chip M1 Pro (CPU 10 cores, GPU 16 cores), RAM 16GB, SSD 1TB
- macOS Montorey 12.2.1
- Python 3.9.8
- PyTorch 1.12


## Prerequisite Installation

### - CMake --> install via conda instead of homebrew
**NOTE**: Compilation needs version 3.13 or greater of cmake.
```
$brew install cmake
```
### - OpenBLAS --> install via conda instead of homebrew
```
$brew install openblas
```
### - Yaml --> install via conda instead of homebrew
```
$python3 -m pip install pyyaml
```

## Download Source-code of PyTorch
```
git clone --recursive https://github.com/pytorch/pytorch
```

Enter to the directory;
```
$cd pytorch
```

## Setting CMakeList.txt -> even without these following changes, I has successfully built and installed PyTorch from source.
At line 184,
Apple Silicon does not support NVIDIA's CUDA;
```
option(USE_CUDA "Use CUDA" OFF)
```

At line 193,
Applie Silicon does not support AMD's ROCm;
```
option(USE_ROCM "Use ROCm" OFF)
```

At line 230,
Apple Silicon does not supprt NVIDIA's NCCL Library;
```
    USE_NCCL "Use NCCL" OFF
```
At line 232,
Apple Silicon does not supprt AMD's RCCL Library;
```
cmake_dependent_option(USE_RCCL "Use RCCL" OFF
```

At line 243,
Apple Silicon does not supprt NUMA Memory;
```
    USE_NUMA "Use NUMA. Only available on Linux." OFF
```


At line 252,
Apple Silicon does not supprt OpenMP;
```
option(USE_OPENMP "Use OpenMP for parallel code" OFF)
```
## Build
### - Compile Sorce-Code
Compile with berrow command;
```
$python3 setup.py build
```
### - Build Wheel
```
$python3 setup.py bdist bdist_wheel
```
## install
Wheel file is in "dist" directory.
You can use **pip install** for the wheel file.
