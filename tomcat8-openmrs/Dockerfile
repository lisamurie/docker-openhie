#############################################################################
# Dockerfile to build Tomcat 8 Server Container images
# Based on Ubuntu
############################################################################


#Set the base image to ubuntu
FROM ubuntu:14.04


#File Author /Maintainer

MAINTAINER Lisa Amai Murie #Label

#################### BEGIN INSTALLATION #######################################

#Set environment variables 
ENV TOMCAT_VERSION_MAJOR 8
ENV TOMCAT_VERSION_FULL 8.5.29	
ENV CATALINA_HOME /opt/tomcat
 
#Install Oracle Java 8

RUN apt-get update && \
apt-get install -y software-properties-common && \
add-apt-repository ppa:webupd8team/java -y && \
apt-get update && \
echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
apt-get install -y oracle-java8-installer && \
apt-get update && \
apt-get clean && \

#Install Apache Tomcat 8 server

groupadd tomcat && \
useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat && \
cd ~ && \
wget http://apache.osuosl.org/tomcat/tomcat-${TOMCAT_VERSION_MAJOR}/v${TOMCAT_VERSION_FULL}/bin/apache-tomcat-${TOMCAT_VERSION_FULL}.tar.gz && \
mkdir /opt/tomcat && \
tar xvf apache-tomcat-${TOMCAT_VERSION_FULL}.tar.gz -C /opt/tomcat --strip-components=1 

#Download openmrs war file

#COPY openmrs.war ${CATALINA_HOME}/webapps/
ADD https://sourceforge.net/projects/openmrs/files/releases/OpenMRS_Platform_1.11.7/openmrs.war ${CATALINA_HOME}/webapps/ 
 
#Change directory to CATALINA_HOME
RUN cd ${CATALINA_HOME}/webapps/ && \
 ls && \
cd ${CATALINA_HOME} && \
chgrp -R tomcat conf && \
chmod g+rwx conf  && \
chmod g+r conf/* && \
chown -R tomcat work/ temp/ logs/ 

EXPOSE 8080

CMD ${CATALINA_HOME}/bin/catalina.sh run

