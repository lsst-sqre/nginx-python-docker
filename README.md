# sqrelsst/nginx-python Docker images

This is an [nginx](http://nginx.org) Docker image built upon the [python:3.5.1 official Python image](https://hub.docker.com/_/python/).
Building nginx upon Python helps save space when deploying nginx with a uWSGI-based Python application that uses the same base image.

This image configures nginx to work with a uWSGI server on an HTTP socket over `3031` port.
By using the HTTP socket it's easy for an nginx container to talk to another uWSGI+app container.

## Image tags

### sqrelsst/nginx-python:compose

Use this image with Docker Compose.
This image configures nginx to work with a uWSGI server over the `uwsgi:3031` HTTP socket.
The `uwsgi` hostname should be set on the uWSGI+App container via Docker Compose.

### sqrelsst/nginx-python:k8s

Use this image with Kubernetes.
On this image, nginx is configured to talk to uWSGI over a `127.0.0.1:3031` HTTP socket since containers in Kubernetes pods all share host network.
The nginx container listens on 8080 because we assume that another service will terminate SSL.

## Prior art

The practices employed in this Docker container are built upon the following repositories and documentation:

- [Official Nginx docker image](https://github.com/nginxinc/docker-nginx/blob/f48d943038eaafd1f69cb14d86db95b3044bd4d8/mainline/jessie/Dockerfile) showed how to install Nginx on Ubuntu in a Dockerfile.
- The [uWSGI docs](http://uwsgi-docs.readthedocs.org/en/latest/Nginx.html#configuring-nginx) included nginx configuration information.
- The [uwsgi-nginx-docker](https://github.com/tiangolo/uwsgi-nginx-docker) image from Sebastián Ramírez showed how to install the nginx configuration.
- 

## License

Copyright 2016 LSST/AURA, MIT Licensed.
