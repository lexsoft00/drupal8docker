FROM drupal:8.3.7

# Install packages
RUN rm /bin/sh && ln -s /bin/bash /bin/sh && \
    apt-get update && apt-get install --no-install-recommends -y \
    curl \
    vim \
    mysql-client

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    ln -s /root/.composer/vendor/bin/drush /usr/local/bin/drush

# Install Drush
RUN composer global require drush/drush && \
    composer global update

# Install Drupal Console
RUN curl https://drupalconsole.com/installer -L -o drupal.phar && \
    mkdir /usr/local/bin/drupal && \
    mv drupal.phar /usr/local/bin/drupal && \
    chmod +x /usr/local/bin/drupal && \
    sed -i '$ a alias drupal="php /usr/local/bin/drupal/drupal.phar"' ~/.bashrc

# Clean repository
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
