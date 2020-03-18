FROM node:dubnium-jessie

# Install Oracle Instant Client
WORKDIR /opt/oracle
ADD https://download.oracle.com/otn_software/linux/instantclient/195000/instantclient-basic-linux.x64-19.5.0.0.0dbru.zip .
RUN apt-get update && \
    apt-get install --no-install-recommends --no-install-suggests -y libaio1 && \
    unzip instantclient-basic-linux.x64-19.5.0.0.0dbru.zip && \
    rm instantclient-basic-linux.x64-19.5.0.0.0dbru.zip && \
    mkdir -p /opt/oracle/ && \
    mkdir -p /etc/ld.so.conf.d/ && \
    echo "/opt/oracle/instantclient_19_5" > /etc/ld.so.conf.d/oracle-instantclient.conf && \
    ldconfig
# Setup Wallet location for oracledb library
#ENV TNS_ADMIN /usr/datastore/oracledb/wallet

WORKDIR /usr/workdir

COPY ./package.json .
RUN npm install

COPY ./HelloWorld.js .

EXPOSE 3000

CMD npm start
