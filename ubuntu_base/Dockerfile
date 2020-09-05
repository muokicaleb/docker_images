FROM ubuntu:18.04

ENV DEBIAN_FRONTEND noninteractive
ENV USER root


RUN apt-get update && \
    apt-get install -y  ubuntu-desktop && \
    apt-get install -y gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal && \
    apt-get install -y tightvncserver && \
    mkdir /root/.vnc

ADD xstartup /root/.vnc/xstartup


# vnc password
RUN printf "password\npassword\n\n" | vncpasswd

RUN mkdir /home/shared

USER root

# Set the locale
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8

CMD /usr/bin/vncserver :1 -geometry 1280x800 -depth 24 && tail -f /root/.vnc/*:1.log

EXPOSE 5901