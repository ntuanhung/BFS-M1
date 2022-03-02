# Reference 
- Created date: 2022/03/02 
- Last update : 2022/03/02

Source from https://developer.apple.com/metal/tensorflow-plugin/

Accelerate training of machine learning models with TensorFlow right on your Mac. Install TensorFlow and the tensorflow-metal PluggableDevice to accelerate training with Metal on Mac GPUs.

PluggableDevice in https://blog.tensorflow.org/2021/06/pluggabledevice-device-plugins-for-TensorFlow.html

## Requirements
- macOS 12.0+ (latest beta version https://beta.apple.com/sp/betaprogram/)

## Not support
- Multi-GPU support
- Acceleration for Intel GPUs
- V1 TensorFlow Networks

## Installation

### Environment setup
- For x86-64 (AMD/Intel-based) -> python 3.8
```
python3 -m venv ~/tensorflow-metal
source ~/tensorflow-metal/bin/activate
python -m pip install -U pip
```

- For ARM64 (Apple Silicon M1) -> python 3.8 and 3.9
```
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
source ~/miniforge3/bin/activate
```

Install tensorflow dependencies for ARM64
```
conda install -c apple tensorflow-deps
```

When upgrading to new base TensorFlow version
```
# uninstall existing tensorflow-macos and tensorflow-metal
python -m pip uninstall tensorflow-macos
python -m pip uninstall tensorflow-metal
# Upgrade tensorflow-deps
conda install -c apple tensorflow-deps --force-reinstall
# or point to specific conda environment
conda install -c apple tensorflow-deps --force-reinstall -n my_env
```

tensorflow-deps versions are following base TensorFlow versions so
```
conda install -c apple tensorflow-deps==2.5.0
```

```
conda install -c apple tensorflow-deps==2.6.0
```

### Tensorflow base (core lib) setup

Via pip
```
python -m pip install tensorflow-macos
```

### Tensorflow Metal (metal plugin) setup

Via pip
```
python -m pip install tensorflow-metal
```

