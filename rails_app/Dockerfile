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

USER ${APP_USER}

WORKDIR ${APP_WD}

ADD supervisor-app.conf ${APP_WD}/supervisor-app.conf

EXPOSE ${APP_PORT}
CMD ["supervisord", "-n", "-c", "supervisor-app.conf"]
