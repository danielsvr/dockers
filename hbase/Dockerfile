FROM danielsvr/debian-java-dotnet-base:latest

ENV HBASE_VERSION	1.2.6

ENV HBASE_DOWNLOAD_URL	http://mirrors.hostingromania.ro/apache.org/hbase/stable/hbase-$HBASE_VERSION-bin.tar.gz

RUN curl $HBASE_DOWNLOAD_URL --output hbase-bin.tar.gz \
    && tar -zxf hbase-bin.tar.gz -C /usr/share \
    && rm hbase-bin.tar.gz 

WORKDIR /usr/share/hbase-$HBASE_VERSION/bin

ENV PATH	"$PATH:/usr/share/hbase-$HBASE_VERSION/bin"

RUN /usr/share/hbase-$HBASE_VERSION/bin/hbase-config.sh

ADD conf /usr/share/hbase-$HBASE_VERSION/conf

RUN mkdir /mnt/volumes/ \
	&& mkdir /mnt/volumes/hbase_data 
	
# zookeeper
EXPOSE 2181
# HBase Master API port
EXPOSE 60000
# HBase Master Web UI
EXPOSE 60010
# Regionserver API port
EXPOSE 60020
# HBase Regionserver web UI
EXPOSE 60030
# HBase Master Second Web UI
EXPOSE 16010



# CMD start-hbase.sh
