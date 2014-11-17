rails_app
=========

Application is located on the host and mounted as volume in container.
This way was we can respawn as many containers as we like.
It also allows us to make changes to the code without the need to enter or recreate
container.

Bundle of gems is installed in separate directory and mounted as volume.
It allows us to reuse the same bundle directory for multiple applications and save space.

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

`docker build -t testapp .`


Running newly created container
------------------------------------

`docker run -d -P -v /home/ak/testapp:/home/ak/testapp -v /home/ak/bundle:/home/ak/bundle testapp`
