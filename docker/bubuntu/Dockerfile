FROM ubuntu:latest

RUN apt update
RUN apt upgrade
RUN apt install -y openssh-server

RUN groupadd -g 1234 tarelka
RUN useradd -u 1234 -g 1234 -m tarelka && yes tarelka | passwd tarelka >/dev/null 2>1

EXPOSE 22
RUN mkdir -p /etc/ssh
RUN echo "StrictHostKeyChecking=no" >> /etc/ssh/ssh_config
RUN mkdir /var/run/sshd 
RUN /usr/bin/ssh-keygen -A
CMD ["/usr/sbin/sshd", "-D"]
