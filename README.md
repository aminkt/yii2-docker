### Yii2 docker files

Docker files and images that created for yii2 light as can.

Most of docker images can use in other project because the strategy to build this images is that
create most light images for grate projects.


### INDEX
* [php7.2-fpm (Base image)](#php7.2-fpm)
* [php7.2-fpm-mongo (Mongodb base image)](#php7.2-fpm)

### PHP7.2-FPM
> You can pull this image by `aminkt/yii2-docker:7.2`

This is the base image that be used by other images based on ubuntu 18.
After using this image you should implement below command to make you container work:
```dockerfile
WORKDIR /app
COPY . /app 
```
The above commands not implemented in base image.


### PHP7.2-FPM-MONGO
> You can pull this image by `aminkt/yii2-docker:7.2-mongo`

This docker file used `PHP7.2-FPM` and add mongo db driver to base image.
Like [PHP7.2-FPM](#php7.2-fpm) you should add below commands to make your docker image useful.
```dockerfile
WORKDIR /app
COPY . /app 
```

### Authors

[Amin Keshavarz](mailto:ak_1596@yahoo.com)

> If you want contribute on this project just clone and create a new poll request.