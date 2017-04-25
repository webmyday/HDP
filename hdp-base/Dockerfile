FROM ubuntu:trusty

RUN apt-get update && apt-get install -y --no-install-recommends \
		bzip2 \
		curl \
		openssh-client \
		wget \
		tar \
		unzip \
		xz-utils \
		python2.7 \
		software-properties-common \
	&& rm -rf /var/lib/apt/lists/*

	
RUN add-apt-repository -y ppa:openjdk-r/ppa && apt-get update \
        && apt-get install -y --no-install-recommends \
        openjdk-8-jdk \
        && update-alternatives --config java && update-alternatives --config javac

        
# add a simple script that can auto-detect the appropriate JAVA_HOME value
# based on whether the JDK or only the JRE is installed
RUN { \
		echo '#!/bin/sh'; \
		echo 'set -e'; \
		echo; \
		echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; \
	} > /usr/local/bin/docker-java-home \
	&& chmod +x /usr/local/bin/docker-java-home

#RUN set -x \
#    export JAVA_HOME=$(docker-java-home)
    
	
