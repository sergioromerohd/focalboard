# Deploy TDT DBBASICO with Docker

## Docker

The Dockerfile gives a quick and easy way to build the latest TDT DBBASICO server and deploy it locally. In the example below,
the TDT DBBASICO database and files will be persisted in a named volumed called `tdt-dbbasico-data`.

From the TDT DBBASICO project root directory:

```bash
docker build -f docker/Dockerfile -t tdt-dbbasico .
docker run -it -v "tdt-dbbasico-data:/opt/focalboard/data" -p 80:8000 tdt-dbbasico
```

Open a browser to [localhost](http://localhost) to start

## Alternative architectures

From the TDT DBBASICO project root directory:

```bash
docker build -f docker/Dockerfile --platform linux/arm64 -t tdt-dbbasico .
docker run -it -v "tdt-dbbasico-data:/opt/focalboard/data" -p 80:8000 tdt-dbbasico
```

## Docker-Compose

Docker-Compose provides the option to automate the build and run step, or even include some of the steps from the [personal server setup](https://www.focalboard.com/download/personal-edition/ubuntu/).

To start the server, change directory to `tdt-dbbasico/docker` and run:

```bash
docker-compose up
```

This will automatically build the TDT DBBASICO image and start it with the http port mapping. These examples also create a persistent named volume called `tdt-dbbasico-data`.

To run TDT DBBASICO with a nginx proxy and a postgres backend, change directory to `tdt-dbbasico/docker` and run:

```bash
docker-compose -f docker-compose-db-nginx.yml up
```
