# BFS-M1
Guidances to build and install different tools/applications on Apple Silicon.

## Guidances
How to setup tensorflow and pytorch on M1. (since 2021/01/29 -> somethings not work now)
https://naturale0.github.io/2021/01/29/setting-up-m1-mac-for-both-tensorflow-and-pytorch

## Tools

### HomeBrew
```
mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
```

Then
```
eval "$(homebrew/bin/brew shellenv)"
brew update --force --quiet
chmod -R go-w "$(brew --prefix)/share/zsh"
```

Note that the one-liner installation method found on brew.sh requires the **Bourne-again shell**, i.e. ***bash***. Notably, ***zsh***, ***fish***, ***tcsh*** and ***csh*** will not work.

### Miniconda
https://docs.conda.io/projects/conda/en/4.6.0/user-guide/install/macos.html


### Tensorflow

### PyTorch

## Applications
- Visual Studio Code - Insiders (Native)
- Docker
- Slack (Native)
- Dropbox (via Rosetta)


## Evaluation
Comparison between the Apple Silicon M1 series and other Intel-based model.
https://towardsdatascience.com/apples-m1-pro-and-m1-max-outperform-google-colab-by-up-to-54-cbf13c8b6357
