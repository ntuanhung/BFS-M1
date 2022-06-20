# MacOS version confirmation
```
sw_vers
```

Result as follows
```
ProductName:	macOS
ProductVersion:	12.4
BuildVersion:	21F79
```

## Rosetta Terminal

Prepare a Rosetta Terminal instance beside the common Terminal
https://www.byran.tech/html/how-to-make-a-rosetta-2-emulated-x86-terminal-on-arm-apple-silicon-chips.html

Change icon of app
https://appleinsider.com/articles/21/01/06/how-to-change-app-icons-on-macos

# Xcode
Install Xcode via Apple Store or HomeBrew


Command Line Tools could be downloaded from here https://developer.apple.com/download/all/?q=command%20line%20tools


Verify the installed Xcode
```
xcode-select -p
```

Verify the installed Command Line Tools
```
clang --version
```

## CreateML

Experience an entirely new way of training machine learning models on your Mac. Create ML takes the complexity out of model training while producing powerful Core ML models.
https://developer.apple.com/machine-learning/create-ml/

- Create Core ML models: Build and train powerful on-device models with an easy-to-use app interface.
- Multimodel training: Train multiple models using different datasets, all in a single project.
- Model previews: Preview your model performance using Continuity with your iPhone camera and microphone on your Mac, or drop in sample data.
- Training control: Pause, save, resume, and extend your training process.
- On-device training: Train models blazingly fast right on your Mac while taking advantage of CPU and GPU.
- eGPU training support: Use an external graphics processing unit with your Mac for even better model training performance.

- **Model types**
Create ML has a variety of model types to choose from. Just select a model type in the app and add your data and parameters to start training.
- **Create ML framework**
The power of Create ML is now available as a Swift framework on iOS and iPadOS, in addition to macOS. Programmatically experiment and automate model creation in Swift scripts or playgrounds. Build dynamic app features that leverage Create ML APIs to train models directly from user input or on-device behavior, providing personalized and adaptive experiences while preserving user privacy.
https://developer.apple.com/documentation/createml

- **Example** Image Classification project https://developer.apple.com/documentation/createml/creating_an_image_classifier_model

# Miniforge (202206 NOT use it -> MiniConda3)
This is a minimalist conda-forge which is easy to install conda packages with different configurations (x86_64 or Apple Silicon) at https://github.com/conda-forge/miniforge


# MiniConda3

Verify the using architecture 
```
uname -m
```

For AARM64: https://docs.conda.io/en/latest/miniconda.html#macos-installers

Move "Initial Code" from .zshrc to .start_miniconda3_aarm64.sh
```
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/<path_to_miniconda3_aarm64>/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/<path_to_miniconda3_aarm64>/etc/profile.d/conda.sh" ]; then
        . "/<path_to_miniconda3_aarm64>/etc/profile.d/conda.sh"
    else
        export PATH="/<path_to_miniconda3_aarm64>/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

For x86_64: using Rosetta Terminal
```
curl -L https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh > Miniconda3-latest-MacOSX-x86_64.sh
sh Miniconda3-latest-MacOSX-x86_64.sh
```

Move "Initial Code" from .zshrc to .start_miniconda3_x86_64.sh
```
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/<path_to_miniconda3_x86_64>/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/<path_to_miniconda3_x86_64>/etc/profile.d/conda.sh" ]; then
        . "/<path_to_miniconda3_x86_64>/etc/profile.d/conda.sh"
    else
        export PATH="/<path_to_miniconda3_x86_64>/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<
```

Copy following code to .zshrc, which enables miniconda3 appropriate with architecture using Terminal
```
# <<<<<< Added by TR 20220405 <<
arch_name="$(uname -m)"
 
if [ "${arch_name}" = "x86_64" ]; then
    echo "Running on Rosetta using miniconda3"
    source ~/.start_miniconda3.sh
elif [ "${arch_name}" = "arm64" ]; then
    echo "Running on ARM64 using miniforge3"
    source ~/.start_miniforge3.sh
else
    echo "Unknown architecture: ${arch_name}"
fi
# <<<<<<<< end <<<<<<<
```

Confirm by following command
```
conda info
```

https://taylorreiter.github.io/2022-04-05-Managing-multiple-architecture-specific-installations-of-conda-on-apple-M1/

# Visual Studio for Mac
This IDE is used to develop and debug the C# console app on MacOS.
https://docs.microsoft.com/en-us/visualstudio/mac/installation?view=vsmac-2019

# Visual Studio Code - Insiders
This IDE is used to develop and debug the Python app on MacOS as well as work on remote servers.
https://code.visualstudio.com/blogs/2016/05/23/evolution-of-insiders

Add Rosetta Terminal to VSCode Profile
https://dev.to/markwitt_me/creating-a-custom-vscode-terminal-profile-for-using-rosetta-on-an-m1-mac-apple-silicon-2gb2

By editing the settings.json file using ```command+shift+P```

```
"terminal.integrated.profiles.osx": {
.......,
  "rosetta": {
    "path": "arch",
    "args": ["-x86_64", "zsh", "-l"],
    "overrideName": true
  }
```

# Tensorflow
TF1 should work on conda x86 version
While conda arm64 version only works with TF2 (--> try to build from source but not success).

TF1.15 --> conda with python3.7, tensorflow-estimator 1.15.1 (this uses CPU-only TF)
