---
layout: post
title: Setup docker on Centos 7 behind proxy
subtitle: Docker installation and proxy setting
tags: [docker]
comments: true
---

## Installation

### Docker Engine

On the server behind corporate server, an easy way  to install Docker fron package (PRM file).

1. Download the package files named docker-ce-\<VERSION_STRING\>, docker-ce-cli-\<VERSION_STRING\>, containerd.io

2. Install them with yum

``` bash
$ sudo yum install /path/to/package.rpm
```

### Docker Compose

1. Run this command to download the current stable release of Docker Compose:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

> To install a different version of Compose, substitute 1.27.4 with the version of Compose you want to use.

2. Apply executable permissions to the binary:

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

3. Create a symbolic link to /usr/bin or any other directory in your path.

```bash
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

## Proxy setup

On CentOS7 if docker is behind a proxy server then use following steps:

1. Create folder for configuring docker service through systemd
``` bash
mkdir /etc/systemd/system/docker.service.d
```

2. Create service configuration file at `/etc/systemd/system/docker.service.d/http-proxy.conf` with the below content.
``` d
[Service]

Environment="HTTP_PROXY=http://YOUR-PROXY.SERVER:PORT/"
Environment="HTTPS_PROXY=http://YOUR-PROXY.SERVER:PORT/"
Environment="FTP_PROXY=http://YOUR-PROXY.SERVER:PORT/"

Environment="NO_PROXY=localhost,127.0.0.0/8,10.0.0.0/8,192.168.0.0/16,172.16.0.0/12"
```

3. Reload systemctl so that new settings are read

``` bash
sudo systemctl daemon-reload
```

4. Verify that docker service Environment is properly set
``` bash
sudo systemctl show docker --property Environment
```

5. Restart docker service so that it uses updated Environment settings
``` bash
sudo systemctl restart docker
```