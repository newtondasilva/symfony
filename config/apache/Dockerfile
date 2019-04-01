FROM 1and1internet/ubuntu-16-apache-php-7.2

COPY cacert.pem /usr/lib/ssl/cacert.pem

# INSTALL NODEJS
RUN apt-get update -yq \
    && apt-get install curl gnupg -yq \
    && curl -sL https://deb.nodesource.com/setup_8.x | bash \
    && apt-get install nodejs -yq
RUN nodejs -v

# INSTALL YARN
RUN curl -sS http://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb http://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update
RUN apt-get install git -y
RUN apt-get install zip -y
RUN apt install yarn -y

RUN composer config --global cafile "/usr/lib/ssl/cacert.pem"

RUN composer global require hirak/prestissimo

RUN ln -s /var/www/html /site
