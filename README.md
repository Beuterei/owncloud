[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <img src="https://owncloud.com/wp-content/uploads/2020/06/oc-logo-1c-1.svg" alt="Logo" height="60">

  <h3 align="center">ownCloud</h3>

  <p align="center">
    Docker setup for ownCloud
    <br />
    <br />
    ·
    <a href="https://github.com/beuluis/owncloud/issues">Report Bug</a>
    ·
    <a href="https://github.com/beuluis/owncloud/issues">Request Feature</a>
  </p>
</p>

<!-- ABOUT THE PROJECT -->

## About The Project

Small docker setup for ownCloud. The production environment also uses [jwilder/nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [nginx-proxy/docker-letsencrypt-nginx-proxy-companion](https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion).

<!-- GETTING STARTED -->

## Getting Started Develop

To get a local copy up and running follow these simple steps.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Installation

1. Clone the repo

```sh
git clone https://github.com/beuluis/owncloud.git
```

2. Start docker-compose

```sh
docker-compose up --build
```

3. Navigate to `localhost:3308`
4. Follow setup instructions

### Customization

1. Create a `.env` file

```sh
touch .env
```

2. Overwrite variables as you like (format: `{variable name}={variable value}`)

| Variable            | Description                               | Default value  | Required |
| ------------------- | ----------------------------------------- | -------------- | -------- |
| `DOMAIN`            | ownCloud domain                           | `localhost`    | false    |
| `OC_ADMIN_USERNAME` | ownCloud admin username                   | `owncloudDev`  | false    |
| `OC_ADMIN_PASSWORD` | ownCloud admin password                   | `7okaKiH6a9km` | false    |
| `PORT`              | Which port is mapped to your host machine | `3308`         | false    |
| `DB_DATABASE`       | Maria DB name                             | `owncloudDev`  | false    |
| `DB_USER`           | Maria user                                | `owncloudDev`  | false    |
| `DB_PASSWORD`       | Maria password                            | `8j38ppKnKNph` | false    |

## Getting Started Production

To get a copy up and running follow these simple steps.

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Nginx by me](https://github.com/beuluis/nginx)

### Installation

1. Clone the repo

```sh
git clone https://github.com/beuluis/owncloud.git --branch master --bare
```

2. Create a `.env.prod` file

```sh
touch .env.prod
```

3. Overwrite all variables marked under Customization as required
4. Start docker-compose

```sh
docker-compose --env-file ./.env.prod -f docker-compose.yml -f docker-compose.production.yml up -d
```

5. Navigate to `https://{your-host}`
6. Follow setup instructions

### Customization

1. Create a `.env.prod` file

```sh
touch .env.prod
```

2. Overwrite variables as you like (format: `{variable name}={variable value}`)

| Variable             | Description                                                     | Default value   | Required |
| -------------------- | --------------------------------------------------------------- | --------------- | -------- |
| `HOST`               | Host which your container should be accessible. E.g. `test.com` | none            | true     |
| `PROXY_NETWORK_NAME` | Proxy network name                                              | `nginxproxynet` | false    |
| `OC_ADMIN_USERNAME`  | ownCloud admin username                                         | none            | true     |
| `OC_ADMIN_PASSWORD`  | ownCloud admin password                                         | none            | true     |
| `DB_DATABASE`        | Maria DB name                                                   | `owncloudProd`  | false    |
| `DB_USER`            | Maria user                                                      | `owncloudProd`  | false    |
| `DB_PASSWORD`        | Maria password                                                  | none            | true     |

## ownCloud maintenance mode

```sh
docker-compose exec {CONTAINER_NAME} occ maintenance:mode --on
```

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- CONTACT -->

## Contact

Luis Beu - me@luisbeu.de

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/beuluis/owncloud.svg?style=flat-square
[contributors-url]: https://github.com/beuluis/owncloud/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/beuluis/owncloud.svg?style=flat-square
[forks-url]: https://github.com/beuluis/owncloud/network/members
[stars-shield]: https://img.shields.io/github/stars/beuluis/owncloud.svg?style=flat-square
[stars-url]: https://github.com/beuluis/owncloud/stargazers
[issues-shield]: https://img.shields.io/github/issues/beuluis/owncloud.svg?style=flat-square
[issues-url]: https://github.com/beuluis/owncloud/issues
[license-shield]: https://img.shields.io/github/license/beuluis/owncloud.svg?style=flat-square
