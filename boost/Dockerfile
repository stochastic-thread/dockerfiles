ARG tag=latest
FROM ubuntu:${tag}
MAINTAINER Luigi Ballabio <luigi.ballabio@gmail.com>
LABEL Description="Provide a building environment where the Boost C++ libraries are available"

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y g++-10 wget libbz2-dev \
 && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 10 \
 && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-10 10 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

ARG boost_version
ARG boost_dir
ENV boost_version ${boost_version}

RUN wget https://dl.bintray.com/boostorg/release/${boost_version}/source/${boost_dir}.tar.gz \
    && tar xfz ${boost_dir}.tar.gz \
    && rm ${boost_dir}.tar.gz \
    && cd ${boost_dir} \
    && ./bootstrap.sh \
    && ./b2 --without-python --prefix=/usr -j 4 link=shared runtime-link=shared install \
    && cd .. && rm -rf ${boost_dir} && ldconfig

CMD bash

