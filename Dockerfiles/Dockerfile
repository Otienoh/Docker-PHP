# Set the base image
FROM 		ubuntu:14.04

MAINTAINER 	Otieno Julie <julie@arifu.com>

#Install dependecies
RUN apt-get update && apt-get -y install apache2 && apt-get -y autoremove && apt-get clean && rm -rf /var/lib/apt/lists/*


EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
 
