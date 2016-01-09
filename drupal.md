# Drupal

Install:

    sudo apt-get install mysql-server php5
    wget https://ftp.drupal.org/files/projects/drupal-8.0.2.tar.gz
    tar -zxvf https://ftp.drupal.org/files/projects/drupal-8.0.2.tar.gz
    sudo mv drupal-8.0.2 /var/www/html/drupal
    cd /var/www/html/drupal
    cp sites/default/default.settings.php sites/default/settings.php
    chmod a+w sites/default
    mysql -u root -p'a' -h localhost -e "
        GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES
        ON drupal0.*
        TO 'root'@'localhost' IDENTIFIED BY 'a';
    "

Edit `settings.php` variable `$database` to match the created MySQL database:

    $databases['default']['default'] = array(
      'driver' => 'mysql',
      'database' => 'drupal0',
      'username' => 'root',
      'password' => 'a',
      'host' => 'localhost',
      'port' => 3306,
      'prefix' => 'prefix0_',
      'collation' => 'utf8mb4_general_ci',
    );

Visit: <http://localhost/drupal>
