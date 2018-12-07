FROM ubuntu:16.04
MAINTAINER AINSD8S

RUN dpkg --configure -a
RUN apt-get update
RUN apt-get -y -q install udev apt-utils ca-certificates wget curl lsb-release rfkill
RUN curl -s --remote-name http://packages.ntop.org/apt/16.04/all/apt-ntop.deb
RUN dpkg -i apt-ntop.deb
RUN rm -rf apt-ntop.deb

RUN apt-get clean all && apt-get update -qq -y
RUN apt-get -y -q install pfring pfring-drivers-zc-dkms ntopng-data cento n2disk ntopng redis-server libpcap0.8 libmysqlclient20 python python-pip

RUN python -m pip install --upgrade pip && python -m pip install setuptools && pip install supervisor

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 3000

RUN echo '#!/bin/bash\n/etc/init.d/redis-server start\nntopng "$@"' > /tmp/run.sh
RUN chmod +x /tmp/run.sh

ENTRYPOINT ["/tmp/run.sh"]

