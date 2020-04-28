ARG tag=latest
FROM lballabio/boost:${tag}
MAINTAINER Luigi Ballabio <luigi.ballabio@gmail.com>
LABEL Description="A development environment for building QuantLib on Travis CI"

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y autoconf automake libtool ccache cmake clang \
 && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 10 \
 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-10 10 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

CMD bash

