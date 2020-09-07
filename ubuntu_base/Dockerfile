FROM ubuntu:18.04

# built-in packages
ENV DEBIAN_FRONTEND noninteractive

ENV USER root


RUN apt-get update 
RUN apt-get install -y --no-install-recommends software-properties-common curl supervisor  net-tools zenity xz-utils dbus-x11 x11-utils alsa-utils mesa-utils libgl1-mesa-dri 
# install debs error if combine together

# Set the locale
# RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
#     locale-gen
# ENV LANG en_US.UTF-8  
# ENV LANGUAGE en_US:en  
# ENV LC_ALL en_US.UTF-8

RUN apt-get update \
    && apt-get install -y --no-install-recommends --allow-unauthenticated \
        xvfb \
        vim-tiny tightvncserver firefox ttf-ubuntu-font-family ttf-wqy-zenhei  

RUN apt-get update \
    && apt-get install -y --no-install-recommends --allow-unauthenticated \
        lxde gtk2-engines-murrine gnome-themes-standard gtk2-engines-pixbuf gtk2-engines-murrine arc-theme 

ADD xstartup /root/.vnc/xstartup


# vnc password
RUN printf "password\npassword\n\n" | vncpasswd

RUN mkdir /home/shared



CMD /usr/bin/vncserver :1 -geometry 1280x800 -depth 24 && tail -f /root/.vnc/*:1.log

EXPOSE 5901