# sqrelsst/nginx-python Docker images

This is an [nginx](http://nginx.org) Docker image built upon the [python:3.5.1 official Python image](https://hub.docker.com/_/python/).
Building nginx upon Python helps save space when deploying nginx with a uWSGI-based Python application that uses the same base image.

## Usage notes

This image configures nginx to work with a uWSGI server over the `uwsgi:3031` HTTP socket.
The `uwsgi` hostname should be set on the uWSGI+App container by an orchestration tool (docker compose can do this via *services*).
By using the HTTP socket it's easy for an nginx container to talk to another uWSGI+app container.

## Prior art

The practices employed in this Docker container are built upon the following repositories and documentation:

- [Official Nginx docker image](https://github.com/nginxinc/docker-nginx/blob/f48d943038eaafd1f69cb14d86db95b3044bd4d8/mainline/jessie/Dockerfile) showed how to install Nginx on Ubuntu in a Dockerfile.
- The [uWSGI docs](http://uwsgi-docs.readthedocs.org/en/latest/Nginx.html#configuring-nginx) included nginx configuration information.
- The [uwsgi-nginx-docker](https://github.com/tiangolo/uwsgi-nginx-docker) image from Sebastián Ramírez showed how to install the nginx configuration.
- 

## License

Copyright 2016 LSST/AURA, MIT Licensed.
