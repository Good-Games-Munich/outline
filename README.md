[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]

<!-- PROJECT HEADER -->
<br />
<p align="center">
  <h3 align="center">Outline</h3>

  <p align="center">
    ·
    <a href="https://github.com/Good-Games-Munich/outline/issues">Report Bug</a>
    ·
    <a href="https://github.com/Good-Games-Munich/outline/issues">Request Feature</a>
    ·
  </p>
</p>

<!-- ABOUT THE PROJECT -->

## About The Project

Setup for outline the wiki software we use to document internal workings and other collaborative work.
Uses discord OpenID Connect for authentication for ease of use.

## Setup

### Production

Will be documented when github action is documented.

### Development

1. Follow the [Customization](#customization) section and set all variables with `Required in dev` `true`.
2. Run `docker-compose up --build`

### Customization

Create a environment file `touch .env.local`. Override variables in the `{variable name}={variable value}` format. All required variables need to be overridden for the respected environment.

| Variable              | Description                                                                                                                                                                                                                                                                     | Required in dev | Required in prod | Default value |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ---------------- | ------------- |
| `SECRET_KEY`          | Run `openssl rand -hex 32` to get one.                                                                                                                                                                                                                                          | `true`          | `true`           | none          |
| `UTILS_SECRET`        | Run `openssl rand -hex 32` to get one.                                                                                                                                                                                                                                          | `true`          | `true`           | none          |
| `POSTGRES_PASSWORD`   | Postgres password. Choose a secure one.                                                                                                                                                                                                                                         | `true`          | `true`           | none          |
| `MINIO_ROOT_PASSWORD` | Minio password. Choose a secure one.                                                                                                                                                                                                                                            | `true`          | `true`           | none          |
| `DISCORD_APP_ID`      | Follow [Discord OpenId Connect](https://fusionauth.io/docs/v1/tech/identity-providers/openid-connect/discord) for a rough tutorial. Id can be retrieved from [Discord Apps](https://discord.com/developers/applications/) > Click your application > OAuth2 > `APPLICATION ID`. | `true`          | `true`           | none          |
| `DISCORD_APP_SECRET`  | Follow [Discord OpenId Connect](https://fusionauth.io/docs/v1/tech/identity-providers/openid-connect/discord) for a rough tutorial. Id can be retrieved from [Discord Apps](https://discord.com/developers/applications/) > Click your application > OAuth2 > `CLIENT SECRET`.  | `true`          | `true`           | none          |
| `MINIO_HOST`          | URL to be used by the reverse proxy. E.g. `minio.domain.de`.                                                                                                                                                                                                                    | `false`         | `true`           | none          |
| `OUTLINE_HOST`        | URL to be used by the reverse proxy. E.g. `wiki.domain.de`.                                                                                                                                                                                                                     | `false`         | `true`           | none          |
| `SMTP_HOST`           | SMTP host.                                                                                                                                                                                                                                                                      | `true`          | `true`           | none          |
| `SMTP_PORT`           | SMTP host.                                                                                                                                                                                                                                                                      | `true`          | `true`           | none          |
| `SMTP_USERNAME`       | SMTP username.                                                                                                                                                                                                                                                                  | `true`          | `true`           | none          |
| `SMTP_PASSWORD`       | SMTP password.                                                                                                                                                                                                                                                                  | `true`          | `true`           | none          |
| `SMTP_FROM_EMAIL`     | SMTP from email.                                                                                                                                                                                                                                                                | `true`          | `true`           | none          |
| `SMTP_REPLY_EMAIL`    | SMTP reply email.                                                                                                                                                                                                                                                               | `false`         | `false`          | ``            |
| `SMTP_TLS_CIPHERS`    | SMTP [tls cipher](https://nodejs.org/api/tls.html#tls_tls_createsecurecontext_options).                                                                                                                                                                                         | `false`         | `false`          | ``            |
| `SMTP_SECURE`         | SMTP secure connection.                                                                                                                                                                                                                                                         | `false`         | `false`          | `1`           |

### Setup a discord application for OpenId Connect

Follow [Discord OpenId Connect](https://fusionauth.io/docs/v1/tech/identity-providers/openid-connect/discord) for a rough tutorial.

1. Navigate to [Discord Apps](https://discord.com/developers/applications/)
2. Create a application
3. Navigate to Your application > OAuth2
4. Click to regenerate a `CLIENT SECRET`
5. Make note of `APPLICATION ID` and `CLIENT SECRET` and set it like described in [Customization](#customization)
6. Add a redirect url with this value: `(http|https)://{url}/auth/oidc.callback`. Make sure to replace url and the protocol according to your environment

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git switch -c feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/:Good-Games-Munich/outline.svg?style=flat-square
[contributors-url]: https://github.com/:Good-Games-Munich/outline/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/:Good-Games-Munich/outline.svg?style=flat-square
[forks-url]: https://github.com/:Good-Games-Munich/outline/network/members
[stars-shield]: https://img.shields.io/github/stars/:Good-Games-Munich/outline.svg?style=flat-square
[stars-url]: https://github.com/:Good-Games-Munich/outline/stargazers
[issues-shield]: https://img.shields.io/github/issues/:Good-Games-Munich/outline.svg?style=flat-square
[issues-url]: https://github.com/:Good-Games-Munich/outline/issues
