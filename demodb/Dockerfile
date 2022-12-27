# The MIT License (MIT)
#
# Copyright (c) 2022 Che-Hung Lin
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

ARG BASE_CONTAINER=mysql:5.7.39

FROM $BASE_CONTAINER

ARG MYSQL_USERNAME
ARG MYSQL_PASSWORD

LABEL maintainer="Che-Hung Lin"

COPY ./my.cnf /etc/mysql/conf.d/my.cnf
COPY ./db.sql /docker-entrypoint-initdb.d/db.sql

WORKDIR /root
RUN chmod 644 /etc/mysql/conf.d/my.cnf && chmod 777 /docker-entrypoint-initdb.d/db.sql
RUN sed -i "s#___user___#${MYSQL_USERNAME}#g" /docker-entrypoint-initdb.d/db.sql; \
    sed -i "s#___pw___#${MYSQL_PASSWORD}#g" /docker-entrypoint-initdb.d/db.sql;

EXPOSE 3306

CMD ["mysqld"]