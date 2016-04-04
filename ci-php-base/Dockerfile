FROM trifs/ci-puppet
MAINTAINER Igor Ajdisek <igor@3fs.si>

RUN export LANG=C.UTF-8 && sudo apt-add-repository -y ppa:ondrej/php5-5.6 && \
    sudo apt-add-repository -y ppa:linuxjedi/ppa   && \
    sudo apt-get update -qq                        && \
    sudo apt-get install -y libuv-dev libgmp-dev   && \
    sudo apt-get install -y openssl libssl-dev     && \
    sudo apt-get install -y php5-intl php5-cli php5-dev php5-curl

# Enable Xdebug and Imagick extensions
RUN printf \\n | sudo pecl -d preferred_state=stable install xdebug && \
    printf \\n | sudo pecl -d preferred_state=stable install imagick && \
    echo "zend_extension=\"`php-config --extension-dir`/xdebug.so\""| sudo tee /etc/php5/cli/conf.d/xdebug.ini && \
    echo "extension=imagick.so" | sudo tee /etc/php5/cli/conf.d/imagick.ini

