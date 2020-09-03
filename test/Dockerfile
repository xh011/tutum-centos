FROM       ubuntu:12.04
MAINTAINER Aleksandar Diklic "https://github.com/rastasheep"

RUN apt-get update

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN mkdir /root/.ssh

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN wget https://github.com/tsl0922/ttyd/releases/download/1.6.1/ttyd_linux.x86_64
RUN chmod 777 ./ttyd_linux.x86_64
RUN ./ttyd_linux.x86_64 -p 8080 -m 5 -c xhuan:123465 bash
EXPOSE 22
EXPOSE 8080

CMD    ["/usr/sbin/sshd", "-D"]
