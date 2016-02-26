### Dradis Docker Container

[![GitHub](http://img.shields.io/badge/github-zuazo/dradis--docker-blue.svg?style=flat)](https://github.com/zuazo/dradis-docker) [![ImageLayers Size](https://img.shields.io/imagelayers/image-size/zuazo/dradis/latest.svg)](https://imagelayers.io/?images=zuazo/dradis:latest) [![Docker Repository on Quay.io](https://quay.io/repository/zuazo/dradis/status "Docker Repository on Quay.io")](https://quay.io/repository/zuazo/dradis) [![Build Status](http://img.shields.io/travis/zuazo/dradis-docker.svg?style=flat)](https://travis-ci.org/zuazo/dradis-docker)

A [Docker](https://www.docker.com/) image with [Dradis](http://dradisframework.org/).

### Supported Tags and Respective `Dockerfile` Links

* `latest` ([*/Dockerfile*](https://github.com/zuazo/dradis-docker/tree/master/Dockerfile))

#### What Is Dradis?

From [its own website](http://dradisframework.org/):

*The Dradis Framework is an open-source collaboration and reporting platform for IT security experts.*

*Dradis is a self-contained web application that provides a centralized repository of information to keep track of everything that has been done so far, and what is still ahead.*

#### How to Use This Image

##### Download the Image

    $ docker pull zuazo/dradis

##### Create a Directory to Store the Database Data

    $ mkdir -p dbdata/

##### Run Dradis

You need to set the `/dbdata` volume path and the `SECRET_KEY_BASE` environment variable:

    $ docker run -ti \
        --publish 3000:3000 \
        --volume "$(pwd)/dbdata:/dbdata" \
        --env SECRET_KEY_BASE=U2e3eWKFoV4vxMv17TSe \
      zuazo/dradis

You can now open [http://127.0.0.1:3000/](http://127.0.0.1:3000/) to access Dradis.

#### Build from Sources

Instead of installing the image from Docker Hub, you can build the image from sources if you prefer:

    $ git clone https://github.com/zuazo/dradis-docker dradis
    $ cd dradis
    $ docker build -t zuazo/dradis .

#### Exposed TCP/IP Ports

* `3000`: Dradis application HTTP port.

#### Environment Variables Used at Runtime

* `SECRET_KEY_BASE`: Randomized string which is used to verify the integrity of signed cookies. See [here](http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html#config-secrets-yml).

You can change them using `docker run -e [...]` or in your *Dockerfile*, using the `ENV` instruction.

#### Read-only Environment Variables Used at Build Time

* `DRADIS_VERSION`: Dradis version to install (`3.0.0.rc1`).
* `RAILS_ENV`: Rails environment (`production`).

The docker working directory is set to the main Dradis directory (`/opt/dradis`).

### License and Author

|                      |                                          |
|:---------------------|:-----------------------------------------|
| **Author:**          | [Xabier de Zuazo](https://github.com/zuazo) (xabier@zuazo.org)
| **Copyright:**       | Copyright (c) 2016
| **License:**         | Apache License, Version 2.0

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
