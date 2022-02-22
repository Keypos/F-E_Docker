FROM mathworks/matlab
ENV DEBIAN_FRONTEND=noninteractive
RUN sudo apt-get update && sudo apt-get install -y wget nano vim tar virtualenv freecad && sudo apt-get purge -y pm-utils xscreensaver* 
RUN sudo wget https://download.jetbrains.com/python/pycharm-community-2021.2.2.tar.gz && sudo tar -xzf pycharm-community-2021.2.2.tar.gz && sudo rm /pycharm-community-2021.2.2.tar.gz
RUN cp /home/matlab/Desktop/MATLAB.desktop /home/matlab/Desktop/PYCHARM.desktop && \
	sed -i 's;Name=.*;Name=Pycharm;' /home/matlab/Desktop/PYCHARM.desktop && \
	sed -i 's;Exec=.*;Exec=/pycharm-community-2021.2.2/bin/pycharm.sh;' /home/matlab/Desktop/PYCHARM.desktop && \
	sed -i 's;Icon=.*;Icon=/pycharm-community-2021.2.2/bin/pycharm.png;' /home/matlab/Desktop/PYCHARM.desktop && \
	sed -i 's;Path=.*;Path=/home/matlab/Documents;' /home/matlab/Desktop/PYCHARM.desktop
RUN cp /usr/share/applications/freecad.desktop /home/matlab/Desktop/freecad.desktop && sudo chmod +x /home/matlab/Desktop/freecad.desktop
RUN cd /opt/matlab/R2021b/extern/engines/python/ && sudo python ./setup.py install
