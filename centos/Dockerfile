FROM ubuntu:latest

RUN apt-get update && \
    apt-get -y install openssh-server && \
    apt-get clean

RUN useradd eman_user && \
    echo 'eman_user:1234' | chpasswd && \
    mkdir -p /home/eman_user/.ssh && chmod 700 /home/eman_user/.ssh

COPY eman-keys.pub /home/eman_user/.ssh/authorized-keys

RUN chown eman_user:eman_user -R /home/eman_user/.ssh && chmod 700 /home/eman_user/.ssh && \
    chmod 600 /home/eman_user/.ssh/authorized-keys

RUN ssh-keygen -A && \
    mkdir /run/sshd

CMD ["/usr/sbin/sshd", "-D"]

