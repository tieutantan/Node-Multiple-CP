# Node Multiple Simple

*The Simple Control Panel For NodeJS Multiple Apps And Domains*

This tool is ideal for individuals who want **a straightforward manner**.

- Run multiple native NodeJS apps and dockerized Nginx.
- With domains on a single server + SSL from CDN.
- A convenient way to create, list, and remove Nginx `.conf` for each domain.
- Easy to run and manage the commands on server boot and multiple ssh keys.

## | [Setup](#setup-nms-in-a-new-aws-ubuntu-server) | [Instruction](#instruction) | [Create Multiple SSH keys](#create-multiple-ssh-keys) |

## Setup NMS

#### 1. Clone this repository.
`git clone https://github.com/tieutantan/Node-Multiple-Simple.git`

#### 2. Move
`cd Node-Multiple-Simple`

#### 3a. Install requires Docker, NodeJS
If Install Docker, Node v19 on AWS Ubuntu v20

`./setup/aws-ubuntu20.sh`

#### 3b. If need run cmd after server reboot (ex: start apps...).

`./setup/run-on-boot.sh`

You can put commands to start any apps to file **Node-Multiple-Simple/auto-run.sh**

Example: auto-run.sh

```
#!/bin/bash

nodemon /path/to/server.js
cd /home/www/domain.com/app
npm run production
pm2 startOrReload /path/other/ecosystem.config.js
```

#### 4. Start
`docker-compose up -d --build`

#### 5. Add, Remove and List your domains, applications.

----

## Instruction

### 1. Add Domain
- `docker exec nms add [domain] [app_local_port]`

Example: tantn.com

- `docker exec nms add tantn.com 1111`

### 2. List Domains as domain-port
- `docker exec nms list`

### 3. Remove Domain
- `docker exec nms remove tantn.com`

----

## Create Multiple SSH Keys

#### 1. Create Key
- `./setup/create-ssh-key.sh [key_name]`
- Example `./setup/create-ssh-key.sh tantn`

#### 2. Add Key to GitHub
- Copy public key display on CMD > add to GitHub Repo > Settings > Deploy keys

#### 3. Clone repository
- Now your repo URL format: `git@[key_name]:USERNAME/repo_name.git`
- Example `git@tantn:tieutantan/repo_name.git`

----

## Others

#### Reload nginx
`docker exec nms nginx -s reload`

----

If you run into a bug or want to work with me to improve it, 
please consider submitting a pull request. 
Your help will be much appreciated by the entire community. Thank you!