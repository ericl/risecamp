FROM jupyter/pyspark-notebook:8ccdfc1da8d5

USER root
RUN mkdir -p /usr/local/bin/start-notebook.d
COPY ./risecamp_start.sh /opt
CMD /opt/risecamp_start.sh

RUN apt-get update
RUN apt-get install -y apt-utils apt-transport-https ca-certificates curl software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
RUN apt-get update && apt-get install -y docker-ce
RUN usermod -aG docker $NB_USER

USER $NB_USER
WORKDIR /home/$NB_USER
RUN rmdir /home/$NB_USER/work
RUN pip install --upgrade pip
