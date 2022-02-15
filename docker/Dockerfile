FROM archlinux:latest

RUN	pacman -Syyu --noconfirm \ 
    pkgconf make git cmake clang gcc \
    gdb neovim lldb openssh valgrind tmux

ENV CXX="/usr/bin/clang++"
ENV CC="/usr/bin/clang"

RUN groupadd -g 1234 tarelka
RUN useradd -u 1234 -g 1234 -m tarelka && yes tarelka | passwd tarelka >/dev/null 2>1

EXPOSE 22
RUN echo "StrictHostKeyChecking=no" >> /etc/ssh/ssh_config
RUN mkdir /var/run/sshd 
RUN /usr/bin/ssh-keygen -A
CMD ["/usr/sbin/sshd", "-D"]
