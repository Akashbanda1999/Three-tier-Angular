FROM  mysql:latest
LABEL app="mysql"
LABEL Author="Akash"

RUN chown -R mysql:root /usr/src/app

ARG MYSQL_DATABASE
ARG MYSQL_USER
ARG MYSQL_PASSWORD
ARG MYSQL_ROOT_PASSWORD

ENV MYSQL_DATABASE=${MYSQL_DATABASE}
ENV MYSQL_USER=${MYSQL_USER}
ENV MYSQL_PASSWORD=${MYSQL_PASSWORD}
ENV MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}

COPY . .

ADD springbackend.sql /etc/mysql/springbackend.sql

RUN sed -i 's/MYSQL_DATABASE/'$MYSQL_DATABASE'/g' /etc/mysql/springbackend.sql    

RUN cp /etc/mysql/springbackend.sql /docker-entrypoint-initdb.d/springbackend.sql

EXPOSE 3306


# HOW to Run the container
# docker run -d -p 3306:3306 --name mysql-container \
# -e MYSQL_DATABASE=studentapp \
# -e MYSQL_USER=mayur \
# -e MYSQL_PASSWORD=1234 \
# -e MYSQL_ROOT_PASSWORD=1234 \
# <imageid>