# Summary
a `.bashrc` file allowing the user to easily run AWS CLI commands in a container with Podman.

# About this project
a `.bashrc` file is a configuration file for the bash shell environment found in the home directory of a user's computer on Linux systems. The `.bashrc` file included in this git repository is the default template used on the Fedora Linux distro, with aliases added for `docker` and `aws`. 

The [`aws-cli`](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) is an open-source command line tool used to interact with [Amazon Web Services](https://aws.amazon.com/). It can be installed directly on your Windows, Mac, or Linux machine. It can also be run from a container. Instructions on how to do the latter can be found [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-docker.html).

Unfortunately, the commands required to run the AWS CLI from a container are long and cumbersome compared to their native counterparts. The `.bashrc` file here can be used to remedy this by allowing the user to run an AWS CLI container from the official Dockerhub image exactly as one would natively - by typing `aws` followed by the command you want to execute. 

# Requirements
To use this file, the user should have podman installed in their machine. Podman is a rootless, daemonless, free and open-source alternative to Docker for managing containers images, and pods. It can be downloaded [here](https://podman.io/).

# How to use this file
Simply copy the file into your home directory. 

Alternately, if you have important information in your existing `.bashrc` file (e.g. `$PATH` variable information used by other applications on your computer) and don't want overwrite your existing `.bashrc` file, simply add the following line to the `\# User specific aliases and functions` section of your file:

`alias aws='podman run --privileged --rm -it -v ~/.aws:/root/.aws -v $(pwd):/aws amazon/aws-cli'`
