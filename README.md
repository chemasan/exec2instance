exec2instance
============
Copyright (c) 2018 Jose Manuel Sanchez Madrid. This file is licensed under MIT license. See file LICENSE for details.

## Overview
exec2instance (execute to ec2 instance) is a tool to easely execute commands on EC2 instances running in the AWS cloud.
AWS Systems Manager Agent has to be installed on the target instances.

## Usage examples
Execute the command "hostname" on the instance with id "i-12345678":
```
exec2instance -i i-12345678 hostname
```

Execute the command "hostname" on the instances with id "i-12345678" and "i-87654321"
```
exec2instance -i i-12345678 -i i-87654321 hostname
```
Execute the command "hostname" on all instances with Name "BackendApp":
```
exec2instance -t Name=BackendApp hostname
```
Execute the command "hostname" on those instances which have a tag "realm" with value "staging" and a tag "cluster" with value "frontend01":
```
exec2instance -t realm=staging -t cluster=frontend01  hostname
```
Execute the command "hostname" on those instances which have a tag "realm" with value "staging" and the tag "cluster" has the value "frontend01" or "frontend04":
```
exec2instance -t realm=staging -t cluster=frontend01 -t cluster=frontend04  hostname
```
Properly pass flags and options to the executed command:
```
exec2instance -i i-12345678  -- ls -ltrah / 
```
This works as well:
```
exec2instance -i i-12345678  "ls -ltrah /"
```

