# BeEF

This directory contains several tutorials and scripts in order to set up a BeEF
(the Browser Exploitation Framework) demo.

See the [tutorial](tutorial.md) for how to **use** the demo. This page shows how
to **set up** and configure the environment.

After following these steps, BeEF will be up and running, as well as Juice Shop.

## Prerequisites

Have `docker` and `docker-compose` installed.

## Startup

In order to start the demo environment, go to this directory, and perform the
following command:

```console
docker-compose up --detach
```

This will build a Docker image with the BeEF application installed, and launch
it as container in the background, listening on
[port 3000](http://127.0.0.1:3000). The first time may be a bit slow, as the
image needs to be built from scratch.

It will also pull a Docker image for Juice Shop, which will be listening on
[port 3500](http://127.0.0.1:3500)

If everything went okay, visiting that page will show you a generic Apache 2
Test Page.

## Host file configuration

In order to make the demo more like a real-world scenario, add the following
entries to the `/etc/hosts` file (note: under Windows, this file can be found
under `C:\Windows\System32\drivers\etc\hosts`):

```
127.0.0.1 beef.local
127.0.0.1 vulnerable.local
```

Now, the BeEF application should be accessible using
[http://beef.local:3000](http://beef.local:3000).

Juice Shop should be accessible using
[http://vulnerable.local:3500](http://vulnerable.local:3500).

## Shutdown

In order to stop the demo environment, go to this, directory, and perform the
following command:

```console
docker-compose down
```

### Configuration

All variables are stored in the `config.yaml` file. Feel free to customize
anything.

## Notes

Please note that this is a demo setup - and not meant to be used in production
in any way. The Docker containers will only bind to the loopback interface,
`127.0.0.1`.
