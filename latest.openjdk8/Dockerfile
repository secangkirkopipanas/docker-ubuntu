FROM ubuntu:latest
MAINTAINER Robertus Lilik Haryanto <robert.djokdja@gmail.com>

# Add repositories
RUN \
	echo "### Add 0x mirror (Singapore)" && \
	echo "deb http://mirror.0x.sg/ubuntu/ xenial main" | tee /etc/apt/sources.list.d/0x-mirror.list && \
    echo "deb-src http://mirror.0x.sg/ubuntu/ xenial main" | tee -a /etc/apt/sources.list.d/0x-mirror.list && \
	echo "deb http://kambing.ui.ac.id/ubuntu/ xenial main" | tee /etc/apt/sources.list.d/kambing.ui.ac.id.list && \
    echo "deb-src http://kambing.ui.ac.id/ubuntu/ xenial main" | tee -a /etc/apt/sources.list.d/kambing.ui.ac.id.list

# Install OpenJDK 8
RUN \
	echo "### Install OpenJDK 8" && \
	apt-get update && apt-get install -y openjdk-8-jdk
	
# Install few applications
RUN \
	echo "### Install few applications"  && \
	apt-get install -y nano wget zip telnet

# Clean apt cache
RUN \
    echo "### Clean up..."  && \
    rm -rf /var/cache/openjdk-8-jdk  && \
    apt-get clean  && \
    rm -rf /var/lib/apt/lists/*

# Setting up environment variables
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
ENV PATH $PATH:$JAVA_HOME/bin
ENV TZ Asia/Singapore

# Define default command
CMD ["/bin/bash"]