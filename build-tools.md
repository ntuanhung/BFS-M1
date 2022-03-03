# MacOS version confirmation
```
sw_vers
```

Result as follows
```
ProductName:	macOS
ProductVersion:	12.2.1
BuildVersion:	21D62
```

## Rosetta Terminal

Prepare a Rosetta Terminal instance beside the common Terminal
https://www.byran.tech/html/how-to-make-a-rosetta-2-emulated-x86-terminal-on-arm-apple-silicon-chips.html

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

# Miniforge
This is a minimalist conda-forge which is easy to install conda packages with different configurations (x86_64 or Apple Silicon) at https://github.com/conda-forge/miniforge


# Visual Studio for Mac
This IDE is used to develop and debug the C# console app on MacOS.
https://docs.microsoft.com/en-us/visualstudio/mac/installation?view=vsmac-2019

# Visual Studio Code - Insiders
This IDE is used to develop and debug the Python app on MacOS as well as work on remote servers.
https://code.visualstudio.com/blogs/2016/05/23/evolution-of-insiders

