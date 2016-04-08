FROM python:3.5.1

MAINTAINER Jonathan Sick <jsick@lsst.org>

# Install nginx.
# Based on https://github.com/nginxinc/docker-nginx/blob/f48d943038eaafd1f69cb14d86db95b3044bd4d8/mainline/jessie/Dockerfile
ENV NGINX_VERSION 1.9.12-1~jessie

RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 \
	&& echo "deb http://nginx.org/packages/mainline/debian/ jessie nginx" >> /etc/apt/sources.list \
	&& apt-get update \
	&& apt-get install -y \
		ca-certificates \
		nginx=${NGINX_VERSION} \
		gettext-base \
	&& rm -rf /var/lib/apt/lists/*

# forward request logs to Docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

# Remove default configuration from Nginx
RUN rm /etc/nginx/conf.d/default.conf

# Copy the modified Nginx conf
COPY nginx.conf /etc/nginx/conf.d/

EXPOSE 80

# Run nginx in foreground to keep the container alive
# Note that nginx alraedy runs itself as non-root
CMD ["nginx", "-g", "daemon off;"]
