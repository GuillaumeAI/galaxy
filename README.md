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

While there isn't necessarily a right or wrong way to organize an Ansible project, there are [best practices](http://docs.ansible.com/ansible/playbooks_best_practices.html), but for the purposes of this example we will divide the project into **_apps_** and **_roles_**. Roles are essentially individual pieces of software while apps are environments which are made up of any number of roles.

We have one example app that contains two items:
- a share folder which is optional, but can be used to share files between the host and the guest (the vm) if necessary
- a `Vagrantfile`, used to configure your Vagrant instance

There are a few important things to note in the `Vagrantfile`:
- The `ip` setting should be set to an available host IP address and should match what you see in the `ansible/inventory/hosts` file
- The `cpus` and `memory` settings should be set as needed, but I believe Vagrant caps these values at 50% of your host's capabilities as a safety measure
- The `ansible.playbook` setting points to the location of the app playbook and within that file you may select the roles you'd like to install (the example only installs style transfer)

#### Boot up the VM
From within the specific apps directory, so for this example `apps/example`, run the following:

`vagrant up`

The first time you do this be prepared to wait as the base ubuntu image needs to be downloaded which is ~1.2GB.

After the image has been downloaded and the VM has been booted up, Vagrant will automatically run the playbook listed in the `Vagrantfile`. The first time you do this can be time consuming so just sit back and grab a beer.

If there are no issues, you will now be able to login to the VM:

`vagrant ssh`

Voilà! Navigate to the folder where Style Transfer has been installed `/opt/style_transfer` (you can configure this location yourself from within the role) and have fun.


## License

Galaxy is [MIT Licensed](../blob/master/LICENSE).
