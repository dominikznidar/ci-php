FROM trifs/ci-php-base:5.6
MAINTAINER Igor Ajdisek <igor@3fs.si>

# Install Cassandra PHP driver 
RUN git clone https://github.com/datastax/php-driver.git && 
    cd php-driver && \
    git reset --hard 1.0.1 && \
    git submodule update --init && \
    cd ext && \
    sudo ./install.sh
RUN echo extension=cassandra.so | sudo tee /etc/php5/cli/conf.d/cassandra.ini

# Ensure cqlsh is available 
RUN wget http://archive.apache.org/dist/cassandra/2.0.16/apache-cassandra-2.0.16-bin.tar.gz && \
    tar xf apache-cassandra-2.0.16-bin.tar.gz && \
    sudo mv apache-cassandra-2.0.16/bin/cqlsh /usr/local/bin/ && \
    sudo mv apache-cassandra-2.0.16/pylib /usr/local/ && \
    rm -rf apache-cassandra-2.0.16* && \
    sudo pip install cql

# Legacy: compile phlacon support for PHP 
RUN git clone https://github.com/phalcon/cphalcon.git && \
    cd cphalcon && \
    git reset --hard phalcon-v1.3.2 && \
    cd build && \
    sudo ./install
RUN echo extension=phalcon.so | sudo tee /etc/php5/cli/conf.d/phalcon.ini
