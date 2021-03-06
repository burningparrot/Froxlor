[![Release](https://img.shields.io/github/v/release/bloodhunterd/froxlor?style=for-the-badge)](https://github.com/bloodhunterd/froxlor/releases)
[![Docker Build](https://img.shields.io/github/workflow/status/bloodhunterd/froxlor/Docker?style=for-the-badge&label=Docker%20Build)](https://github.com/bloodhunterd/froxlor/actions?query=workflow%3ADocker)
[![Docker Pulls](https://img.shields.io/docker/pulls/bloodhunterd/froxlor?style=for-the-badge)](https://hub.docker.com/r/bloodhunterd/froxlor)
[![License](https://img.shields.io/github/license/bloodhunterd/froxlor?style=for-the-badge)](https://github.com/bloodhunterd/froxlor/blob/master/LICENSE)

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/bloodhunterd)

# Froxlor

Docker image for Froxlor Server Management Panel.

## Features

* [NGINX](https://www.nginx.com/) webserver support
* [PHP](https://www.php.net/) 7.3, 7.4 and 8.0 support
* [BIND](https://www.isc.org/bind/) DNS support
* [Let's Encrypt](https://letsencrypt.org/) SSL certificate support

## Deployment

Download Froxlor from the Froxlor website and mount it into the container for individually setup.

[![Froxlor website](https://img.shields.io/badge/Froxlor-Website-blue?style=for-the-badge)](https://froxlor.org/)

### Docker Compose

```dockerfile
version: '2.4'

services:
  froxlor:
    image: bloodhunterd/froxlor
    ports:
      - '80'
      - '443'
    restart: unless-stopped
    volumes:
      - ./froxlor/:/var/www/froxlor/
      - ./customers/:/var/customers/
      - ./ssl/:/etc/ssl/froxlor/

```

### Configuration

| ENV | Values | Default | Description
| --- | ------- | ------- | -----------
| TZ | [PHP: List of supported timezones - Manual](https://www.php.net/manual/en/timezones.php) | Europe/Berlin | Timezone

### Ports

| Port | Description
| ---: | -----------
| 53 | Bind DNS
| 80 | HTTP
| 443 | HTTPS

### Volumes

| Volume | Path | Read only | Description
| ------ | ---- | :-------: | -----------
| Froxlor | /var/www/froxlor/ | &#10008; | Froxlor Server Management Panel. *Need to persist to use the build in update process.*
| Customers | /var/customers/ | &#10008; | Froxlor customer web, mail and log contents.
| SSL certificates | /etc/ssl/froxlor/ | &#10008; | [Let's Encrypt](https://letsencrypt.org/de/) SSL certificates.

| &#10004; Yes | &#10008; No
| ------------ | -----------

## Update

Please note the [changelog](https://github.com/bloodhunterd/froxlor/blob/master/CHANGELOG.md) to check for configuration changes before updating.

```bash
docker-compose pull
docker-compose up -d
```

## Build With

* [Froxlor](https://froxlor.org/)
* [NGINX](https://www.nginx.com/)
* [MariaDB](https://mariadb.org/)
* [PHP](https://www.php.net/)
* [BIND](https://www.isc.org/bind/)
* [Let's Encrypt](https://letsencrypt.org/)
* [Debian](https://www.debian.org/)
* [Docker](https://www.docker.com/)

## Authors

* [BloodhunterD](https://github.com/bloodhunterd)

## License

This project is licensed under the MIT - see [LICENSE.md](https://github.com/bloodhunterd/froxlor/blob/master/LICENSE) file for details.
