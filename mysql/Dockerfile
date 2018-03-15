#############################################################################
# Dockerfile to build MongoDB Container images
# Based on Ubuntu
############################################################################


#Set the base image to ubuntu
FROM ubuntu:14.04


#File Author /Maintainer

MAINTAINER Lisa Amai Murie #Label

#################### BEGIN INSTALLATION #######################################

#Set environment variables 
ENV MYSQL_VERSION_FULL 5.6
 
RUN apt-get update && \
apt-get install -y software-properties-common && \
add-apt-repository ppa:webupd8team/java -y && \
apt-get update && \
echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
apt-get install -y oracle-java8-installer && \
apt-get update && \
apt-get install mysql-server-${MYSQL_VERSION_FULL} -y  && \
apt-get update && \
apt-get clean && \

VOLUME /var/lib/mysql

EXPOSE 3306

CMD ["mysqld"]

