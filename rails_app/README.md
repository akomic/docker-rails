rails_app
=========

Running Docker container with Rails and Unicorn
-----------------------------------------------------------

Application is located on the host and mounted as volume in container.
This way we can respawn as many containers as we like.
It also allows us to make changes to the code without the need to enter or recreate
container.

Bundle of gems is installed in separate directory and mounted as volume.
It allows you to reuse the same bundle directory for multiple applications and save space and time.

ubuntu_rails image is required
------------------------------

Edit Dockerfile to reflect your setup.
-------------------------------------

### Current one assumes the following:

* Name of application: testapp
* Location of the Rails application on the host: /home/ak/testapp
* Location of the bundle directory on the host: /home/ak/bundle


Building testapp image
----------------------

`$ docker build -t testapp .`

Bundling
--------

To bundle we are going to run separate container

```
$ docker run -t -i -P \
  --env RAILS_ENV="development" \
  --env SECRET_KEY_BASE="<here_goes_secret_key>" \
  -v /home/ak/testapp:/home/ak/testapp -v /home/ak/bundle:/home/ak/bundle \
  --name testappBundler testapp /bin/bash
```

```
ak@16d2c0b666a3:~/testapp$ bundle install --path /home/ak/bundle/
ak@16d2c0b666a3:~/testapp$ exit
```

Running newly created container with unicorn
--------------------------------------------

```
$ docker run -d -p 14401:14401 \
  --env RAILS_ENV="development" \
  --env SECRET_KEY_BASE="<here_goes_secret_key>" \
  -v /dev/log:/dev/log \
  -v /home/ak/testapp:/home/ak/testapp -v /home/ak/bundle:/home/ak/bundle \
  --name testapp testapp
```

```
$ docker logs testapp
2014-11-17 16:06:41,216 INFO spawned: 'railsapp' with pid 9
2014-11-17 16:06:43,004 INFO success: railsapp entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
```

Application is ready listening on port 14401 on all ip addresses on the server.
