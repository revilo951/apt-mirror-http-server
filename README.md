# apt-mirror-http-server

[![Docker Stars](https://img.shields.io/docker/stars/robinlennox/apt-mirror-http-server.svg)](https://hub.docker.com/r/robinlennox/apt-mirror-http-server/)
[![Docker Pulls](https://img.shields.io/docker/pulls/robinlennox/apt-mirror-http-server.svg)](https://hub.docker.com/r/robinlennox/apt-mirror-http-server/)

Using Docker to construct your APT(Advanced Packaging Tools) mirror HTTP server.

## Usage
### Basic command:

```
docker run -d --name apt-mirror \
           -v /path/data:/var/spool/apt-mirror \
           -p 8080:80 robinlennox/apt-mirror-http-server
```

* `-v /path/data`: the path which you want to store data


### More options with docker command

* `-v /path/your/mirror.list:/etc/apt/mirror.list`: to replace [Ubuntu default mirror.list](https://github.com/robinlennox/apt-mirror-http-server/blob/master/mirror.list)
* `-e RESYNC_PERIOD=timeout-value`: to set the resync period, default is 12 hours. To set the [TIMEOUT format description](http://www.cyberciti.biz/faq/linux-unix-sleep-bash-scripting/)

## Changelog

* 2020-07-31: version 0.1.3
  * Updated for focal

* 2017-07-27: version 0.1.2
  * Fix the container started twice: "httpd (pid 13) already running"

* 2017-04-28: version 0.1.1
  * Fix http server doesn't start after the container restarted

* 2017-04-27: version 0.1
  * Update base image to Ubuntu 16.04
  * remove option `MIRROR_URL`
  * rename `TIMEOUT` environment value to `RESYNC_PERIOD`
  * fix issue [#1 https isn't handle correctly in setup.sh](https://github.com/seterrychen/apt-mirror-http-server/issues/1)
