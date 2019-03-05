FROM ubuntu:bionic
MAINTAINER AINSSD8S
#LATEST UBUNTU#
RUN dpkg --configure -a
RUN apt-get update
RUN apt-get -y -q install apt-utils ca-certificates wget curl lsb-release gnupg
RUN curl -s --remote-name http://packages.ntop.org/apt/18.04/all/apt-ntop.deb
RUN dpkg -i apt-ntop.deb
RUN rm -rf apt-ntop.deb

RUN apt-get clean all && apt-get update -qq -y
RUN apt-get -y -q install pfring-dkms nprobe cento n2disk ntopng redis-server libpcap0.8 libmysqlclient20
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 3000

RUN echo '#!/bin/bash\n/etc/init.d/redis-server start\nntopng "$@"' > /tmp/run.sh
RUN chmod +x /tmp/run.sh

ENTRYPOINT ["/tmp/run.sh"]
