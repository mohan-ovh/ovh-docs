---
title: 'Preparing an environment for using the OpenStack API'
slug: prepare_the_environment_for_using_the_openstack_api
excerpt: 'Install the OpenStack environment to manage your instances via the API'
section: OpenStack
order: 1
updated: 2022-03-30
---

**Last updated 30th March 2022**

## Objective

You can manage Public Cloud services using commands sent from the system console, once you have downloaded and installed OpenStack tools.

With the OpenStack API, you can automate your management by generating scripts. The OpenStack Nova client can be used to manage instances and disk space. With the OpenStack Glance client, you can manage images and backups, while the Swift client can be used to manage object storage space.

**Find out how to install these OpenStack tools.**

## Requirements

- **Root** access to the environment you want to configure

## Instructions

### On Debian

Open the terminal and connect to the environment you want to prepare via SSH.

Update the packet cache using the `apt update` command:

```sh
apt update
```

Use the command below to install the OpenStack client, as well as Nova client (compute application) and Swift using python3-pip:

```sh
apt install python3-pip -y
pip3 install --upgrade pip
pip3 install python-openstackclient python-novaclient python-swiftclient
```

After you have completed this step, we recommend creating a special user without root access.

To access the help tools, run the following command:

```sh
openstack --help
nova help
```

> [!primary]
>
> The documentation for the OpenStack API is available [here](https://docs.openstack.org/python-openstackclient/latest/){.external}.
>

### On CentOS

Open the terminal and connect to the environment you want to prepare via SSH.

Update the packet cache using the following command:

```sh
yum update -y
```

Use the command below to install the OpenStack client, as well as Nova client (compute application) and Swift using python3-pip:

```sh
yum install python3-pip -y
pip3 install --upgrade pip
pip3 install python-openstackclient python-novaclient python-swiftclient
```

After you have completed this step, we recommend creating a special user without root access.

To access the help tools, run the following command:

```sh
openstack --help
nova help
```

> [!primary]
>
> The documentation for the OpenStack API is available [here](https://docs.openstack.org/python-openstackclient/latest/){.external}.
>

### On Windows

Download and install Python version 2.7.14. You can choose to add the Python programming language automatically to Path, by ticking this option in the installation configuration:

![Automatic installation](images/1_preparation_openstack_environment_windows.png){.thumbnail}

You can also install it yourself. To do this, follow the actions described below:

#### Step 1: Edit the system’s environment variables.

Search for the system’s environment variable settings, and go to “Edit the system environment variables”:

![Environment variable settings](images/2_preparation_openstack_environment_windows.png){.thumbnail}

#### Step 2: Edit the system settings.

Go to the `Advanced`{.action} tab, and click `Environment Variables`{.action} to edit the settings.

![Performance settings](images/3_preparation_openstack_environment_windows.png){.thumbnail}

#### Step 3: Configure the environment variables.

In the ‘System variables’ section, select ‘New’, attribute the name “PYTHON_HOME”, and add the access path to Python. By default, it will be: ‘C:\\Python27’.

![Add the access path](images/4_edit_system_variables.png){.thumbnail}

#### Step 4: Add the path for the variables.

Once you have added Python, edit the ‘Path’ field in the system variables, and add the following to the end of the path:

`...;%PYTHON_HOME%\;%PYTHON_HOME%\Script`

#### Step 5: Restart Windows.

The changes you have made will become effective after the system has been rebooted.

#### Step 6: Install the OpenStack client.

As an administrator, open the program in the command line (CMD), and install the OpenStack client using the following command:

```sh
pip install python-openstackclient
```

If the operation is completed properly, you will see a summary:

![Automatic installation](images/5_preparation_openstack_environment_windows.png){.thumbnail}

You can check the installation version in the CMD (command line) window that has just opened, by entering ‘python-V’ from any system location.

![Checking](images/6_preparation_openstack_environment_windows.png){.thumbnail}

### On MacOS

You can use [HomeBrew](https://brew.sh), a package manager for MacOS.

Open the terminal and execute the following command:

```bash
brew install openstackclient
```

Use the command below to install the Nova client (compute application) and Swift:

For Python2:

```sh
pip install python-novaclient
pip install python-swiftclient
```

For Python3:

```sh
pip3 install python-novaclient
pip3 install python-swiftclient
```

To access the help tools, run the following command:

```sh
openstack --help
nova help
```

## Go further

[Setting OpenStack environment variables](https://docs.ovh.com/ie/en/public-cloud/set-openstack-environment-variables/).

Join our community of users on <https://community.ovh.com/en/>.
