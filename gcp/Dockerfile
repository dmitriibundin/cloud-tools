FROM ubuntu:18.04

WORKDIR /root

RUN apt-get update && apt-get install -y \
                      curl \
                      gnupg2 \
                      git \
                      maven \
                      openjdk-8-jdk \
                      python3 \
                      python3-pip \
                      #To run legacy code that cannot be run with python3
                      python2.7 \
                      python-pip \
                      net-tools \
                      nginx

RUN pip3 install apache-beam[gcp] && \
pip3 install oauth2client==3.0.0 && \
pip3 install -U pip

RUN pip2 install apache-beam[gcp] && \
pip2 install oauth2client==3.0.0 && \
pip2 install -U pip

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y vim-gtk

RUN update-java-alternatives --set /usr/lib/jvm/java-1.8.0-openjdk-amd64

RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] http://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -

RUN apt-get update && apt-get install -y google-cloud-sdk  \
                                         google-cloud-sdk-datalab

CMD ["/bin/bash"]
