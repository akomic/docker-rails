ubuntu_rails
------------

Creating basic ubuntu image with tools and packages needed to run rails application.

### Edit Dockerfile

and specify default user under which application is going to run

### Create image

`$ docker build -t ubuntu_rails .`

```
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
ubuntu_rails        latest              c53d4c49713d        6 seconds ago       455.5 MB
ubuntu              latest              5506de2b643b        3 weeks ago         199.3 MB
```
