FROM almalinux

RUN dnf -y install openssh-server sudo passwd

RUN useradd guacamole && \
    /usr/bin/ssh-keygen -A

WORKDIR /home/guacamole

CMD /usr/sbin/sshd -D
