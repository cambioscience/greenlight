# Greenlight

![Travis CI](https://travis-ci.org/bigbluebutton/greenlight.svg?branch=master)
![Coverage
!Status](https://coveralls.io/repos/github/bigbluebutton/greenlight/badge.svg?branch=master)
![Docker Pulls](https://img.shields.io/docker/pulls/bigbluebutton/greenlight.svg)

Greenlight is a simple front-end interface for your BigBlueButton server. At it's heart, Greenlight provides a minimalistic web-based application that allows users to:

  * Signup/Login with Google, Office365, or through the application itself.
  * Manage your account settings and user preferences.
  * Create and manage your own personal rooms ([BigBlueButton](https://github.com/bigbluebutton/bigbluebutton) sessions).
  * Invite others to your room using a simple URL.
  * View recordings and share them with others.

Interested? Try Greenlight out on our [demo server](https://demo.bigbluebutton.org/gl)!

Greenlight is also completely configurable. This means you can turn on/off features to make Greenlight fit your specific use case. For more information on Greenlight and its features, see our [documentation](http://docs.bigbluebutton.org/greenlight/gl-install.html).

For a overview of how Greenlight works, checkout our Introduction to Greenlight Video:

[![GreenLight Overview](https://img.youtube.com/vi/Hso8yLzkqj8/0.jpg)](https://youtu.be/Hso8yLzkqj8)

## Development environment

1. Configure `.env` file

Set mandatory fields:
 * `SECRET_KEY_BASE`
 * `BIGBLUEBUTTON_ENDPOINT`
 * `BIGBLUEBUTTON_SECRET`

See [`sample.env`](https://github.com/cambioscience/greenlight/blob/master/sample.env) file to see how to do it properly.

2. Build new image and remove old ones 

```sh
 $ docker build --tag cambioscience/greenlight:release-v2 --file dev.Dockerfile .
 $ docker image prune
```

3. Run containers

In the root project directory run in command line:

```sh
  $ docker-compose --file docker-compose-dev.yml up -d
```

4. Enter running greenlight container

```sh
  $ docker exec -it greenlight-v2 /bin/bash
```

5. You can see your application running here: http://127.0.0.1:5000

6. You can attach to a running container

```sh
  $ docker attach greenlight-v2
```

## Installation on a BigBlueButton Server

Greenlight is designed to work on a [BigBlueButton 2.0](https://github.com/bigbluebutton/bigbluebutton) (or later) server.

For information on installing Greenlight, checkout our [Installing Greenlight on a BigBlueButton Server](http://docs.bigbluebutton.org/greenlight/gl-install.html#installing-on-a-bigbluebutton-server) documentation.

## Deployment

1. Stop Greenlight docker containers.
2. Restart Big Blue Button.
3. Run script for image build and deployment.

```sh
  $ sudo docker-compose down
  $ sudo bbb-conf --restart
  $ sudo ./scripts/build-and-deploy.sh
```

## Source Code & Contributing

Greenlight is built using Ruby on Rails. Many developers already know Rails well, and we wanted to create both a full front-end to BigBlueButton but also a reference implementation of how to fully leverage the [BigBlueButton API](http://docs.bigbluebutton.org/dev/api.html).

We invite you to build upon Greenlight and help make it better. See [Contributing to BigBlueButton](http://docs.bigbluebutton.org/support/faq.html#contributing-to-bigbluebutton).

We invite your feedback, questions, and suggests about Greenlight too. Please post them to the [developer mailing list](https://groups.google.com/forum/#!forum/bigbluebutton-dev).