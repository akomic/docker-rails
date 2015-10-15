# Copyright 2014 Alen Komic
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM ubuntu_rails

MAINTAINER akomic

ENV APP testapp
ENV APP_USER ak
ENV APP_WD /home/${APP_USER}/${APP}
ENV APP_PORT 14401


# Adding user to sudo group and setting password to 'mypass' CHANGE IT!
RUN usermod -a -G sudo ${APP_USER}
RUN echo "${APP_USER}:mypass" |chpasswd

USER ${APP_USER}

WORKDIR ${APP_WD}

EXPOSE ${APP_PORT}

CMD bundle exec unicorn -p $APP_PORT -c ./config/unicorn.rb
