# Ansible deployment for Bamboo

## 0. Current Stats

[![Build Status](https://travis-ci.org/configuresystems/ansible-bamboo.svg)](https://travis-ci.org/configuresystems/ansible-bamboo)

|    Name         |    Description            |
| --------------- | ------------------------- |
| Version         | 0.1                       |
| Updated         | 03.22.2015                |
| Ansible Version | 1.8.4                     |
| Author          | Johnny Martin             |
| Website         | http://configure.systems/ |
| License         | MIT                       |


## 1. QuickStart

```bash
git clone https://github.com/configuresystems/ansible-bamboo.git roles/ansible-bamboo
# Create a playbook file to use, there's a sample one in tests/test.yml
# Create a group_vars or update the default values in defaults/main.yml
ansible-playbook -i path/to/inventory ansible-bamboo.yml
```

    
## Table of contents

- [1. QuickStart](#1-quickstart)
- [2. Overview](#2-overview)
- [3. Requirements](#3-requirements)
  - [3.1 Ubuntu](#31-ubuntu)
  - [3.2 Compile from Source](#32-compile-from-source)
- [4. Usage](#4-usage)
  - [4.1 Playbook Arguments](#41-playbook-arguments)
  - [4.2 Not Currently in Use](#41-not-currently-in-use)
- [5. After Install](#5-after-install)
- [6. Bamboo Control](#6-bamboo-control)
  - [6.1 Stop](#61-stop)
  - [6.2 Start](#62-start)
  - [6.3 Restart](#63-restart)


## 2. Overview

An Ansible playbook to automate the installation of Atlassian Bamboo.

It uses the self installer along with the response.varfile to automate
the installation.


## 3. Requirements

Ansible installed on the local machine.

#### 3.1 Ubuntu

```bash
pip install ansible
```

#### 3.2 Compile from Source

```bash
git clone git://github.com/ansible/ansible.git --recursive
cd ./ansible
source ./hacking/env-setup
```

## 4. Usage

1. `git clone http://github.com/configuresystems/ansible-bamboo`
2. Create a vars file in your group_vars, host_vars, set vars in the Playbook,
   or update the 'defaults/main.yml' file
3. run the Ansible playbook, the fastest way is:

```bash
ansible-playbook ansible-bamboo.yml
```

### 4.1 Playbook Arguments

- bambooControl: bamboo Controller Port
- bambooHttp: Accessible bamboo Port
- bambooHome: The home dir of bamboo, not the install dir
- bambooData: Install dir of bamboo
- bambooTarFile: Name of the bin autoinstaller
- bambooUrl: Location of where bamboo is to be downloaded from
- mysqlConnectorJar: In order to use MySQL, a plugin must be added, 
                     this is that file
- mysqlConnectorUrl: Where to download the the connector plugin from
  
### 4.2 Not Currently in use
- mysqlHost: Host of the database to utilize 
- mysqlPort: Database port
- mysqlDatabase: Database Name
- mysqlUser: Database User
- mysqlPasswd: Database Passwd


### 5. After install

Visit the bamboo server via the browser by going to:

http://your.ip.address.yes:{{ bambooHttp }}

Finish up the install process by adding the database info and
product key probvided by Atlassian.

### 6. bamboo Control

#### 6.1 Stop

```bash
service bamboo stop
```

#### 6.2 Start

```bash
service bamboo start
```

#### 6.3 Restart

```bash
service bamboo restart
```
