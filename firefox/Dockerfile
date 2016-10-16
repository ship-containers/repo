FROM ubuntu:16.04

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y firefox sudo

RUN export uid=1000 gid=1000 && \
    mkdir -p /home/user && \
    echo "user:x:${uid}:${gid}:Developer,,,:/home/user:/bin/bash" >> /etc/passwd && \
    echo "user:x:${uid}:" >> /etc/group && \
    echo "user ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/user && \
    chmod 0440 /etc/sudoers.d/user && \
    chown ${uid}:${gid} -R /home/user

USER user
ENV HOME /home/user
ENTRYPOINT ["/usr/bin/firefox"]
