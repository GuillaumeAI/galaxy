# Galaxy

Galaxy is a provisioning environment for various machine/deep learning software and is intended mainly for local development/experimentation. Currently, the following are available for set-up:

- [Berkeley Caffe](http://caffe.berkeleyvision.org/)
- [Neural Style](https://github.com/jcjohnson/neural-style)
- [OpenCV 3.1.0](http://opencv.org/)
- [Style Transfer](https://github.com/fzliu/style-transfer)
- [Deep Visualization Toolbox](http://yosinski.com/deepvis)

#### Caveats
This tool is for Mac OSX only at the moment. While familiarity with [Ansible](https://www.ansible.com/) and [Vagrant](https://www.vagrantup.com/) are not mandatory for set-up, any experience with these provisioning tools will be helpful when attempting to edit/improve/debug the code. One final important note - currently the provisioning steps for any of the above listed software default to a CPU-only installation, as it is assumed that the set-up will be done on a personal machine. A command-line option to switch to a GPU-based installation will be added eventually for those with CUDA enabled graphics cards.

## Prerequisites

#### Package Manager
- Homebrew
- Homebrew Cask

Installation of homebrew and cask will not be covered but can be found [here](https://brew.sh/) and [here](https://caskroom.github.io/).

#### Python/pip
If you don't already have python and pip installed:

`brew install python`

#### Provisioning Tools
- Vagrant - For local, portable development environments
- Virtualbox - Free VM software that acts as a provider for Vagrant (VMWare Fusion is another popular option but requires a license AND a plug-in which also costs money)
- Ansible - For automating software installation/configuration

Install vagrant:

`brew cask install vagrant`

Install virtualbox:

`brew cask install virtualbox`

Install ansible:

`pip install ansible`

## Getting Started
