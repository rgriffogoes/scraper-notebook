[![Build, test, and publish Docker Images](https://github.com/rgriffogoes/scraper-notebook/actions/workflows/docker.yml/badge.svg)](https://github.com/rgriffogoes/scraper-notebook/actions/workflows/docker.yml)

# scraper-notebook
scraper-notebook is a community maintained Jupyter Docker Stack image that aims to provide an environment suitable for web scraping development - including web driver, requests and others (see Dockerfile for details)

# Running
Run like any standard JupyterLab docker noteboooks:

```
docker run -p8888:8888 rgriffogoes/scraper-notebook
```

Or with persistent storage and as a Daemon:

```
docker run -p8888:8888 -d -v ~/notebook:/home/jovyan/work rgriffogoes/scraper-notebook
```

If you are having issues with web driver scraper and "big" pages, set the shm size:

```
docker run -p8888:8888 -d -v ~/notebook:/home/jovyan/work --shm-size=512mb  rgriffogoes/scraper-notebook
```

Or yet with a Docker compose file:
```
version: "3"
services:
  scraper-notebook:
    image: rgriffogoes/scraper-notebook
    container_name: scraper-notebook
    env_file:
      - .env
    ports:
      - 8888:8888
    volumes:
      - ~/notebook:/home/jovyan/work
    restart: unless-stopped
    shm_size: '256mb'

```
And accompanying .env file for simple+insecure password (fine for secure local instances - and no log reading for getting token):
```
JUPYTER_TOKEN=mypassword
```

# Jupyter Docker Stacks - Community Stack version
This project is developed with the helpful guide of [Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/). The base container is **jupyter/minimal-notebook** and this **Community Stack** is setup [via the guide.](https://jupyter-docker-stacks.readthedocs.io/en/latest/contributing/stacks.html)
