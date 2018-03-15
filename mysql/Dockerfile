#############################################################################
# Dockerfile to build MySQL Server  Container images
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
apt-get install mysql-server-${MYSQL_VERSION_FULL} -y  && \
apt-get update && \
apt-get clean

VOLUME /var/lib/mysql

EXPOSE 3306

CMD ["mysqld"]

