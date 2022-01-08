FROM ubuntu:latest
ENV TZ=Europe/Berlin
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y sudo freecad x11vnc xvfb xfce4 xfce4-goodies dbus-x11
RUN apt-get purge -y pm-utils xscreensaver*
ARG user=user
ARG home=/home/$user
ARG pass=default
RUN useradd --create-home -s /bin/bash $user \
        && echo $user:$pass | chpasswd \
        && adduser $user sudo
RUN echo "Xvfb -screen 0 1900x900x24 -ac & \
	sleep 5 && \
	startxfce4 & \
	sleep 5 && \
	freecad & \
	x11vnc -forever" > /entrypoint.sh &&\
	chmod +x /entrypoint.sh
ENV DISPLAY=:0.0
USER user
ENTRYPOINT ["sh", "/entrypoint.sh"]

