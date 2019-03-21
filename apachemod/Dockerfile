FROM lephare/apache


#Install needed packages for RadStudio and some utils
RUN \
	apt-get -y update && \
	apt-get -y upgrade && \
	apt-get -y dist-upgrade && \
	apt-get -y install joe wget p7zip-full curl unzip build-essential zlib1g-dev libcurl4-gnutls-dev && \
	apt-get -y install mysecureshell && \
	apt-get -y autoremove && \
	apt-get -y autoclean

RUN touch /etc/apache2/sites-enabled/default.conf \
    && echo "<VirtualHost *:80>" >> /etc/apache2/sites-enabled/default.conf \
    && echo "  ServerAdmin webmaster@localhost" >> /etc/apache2/sites-enabled/default.conf \
    && echo "  DocumentRoot /var/www/html" >> /etc/apache2/sites-enabled/default.conf \
    && echo "  CustomLog /var/log/apache2/access.log common" >> /etc/apache2/sites-enabled/default.conf \
    && echo "</VirtualHost>" >> /etc/apache2/sites-enabled/default.conf 

RUN mkdir /etc/apache2/mods-custom \ 
    && echo "IncludeOptional mods-custom/*.load" >> /etc/apache2/apache2.conf \
    && echo "IncludeOptional mods-custom/*.conf" >> /etc/apache2/apache2.conf 