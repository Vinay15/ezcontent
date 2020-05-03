pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''rm -rf ezcontent-blt;
        COMPOSER_MEMORY_LIMIT=-1 composer create-project --no-interaction acquia/blt-project ezcontent-blt;
        cd ezcontent-blt;
        composer require srijanone/ezcontent:8.x-dev#559493;
        mkdir -p docroot/sites/default/files; chmod -R 777 docroot/sites/default/files; mkdir -p private-files; chmod -R 777 private-files; cp docroot/sites/default/default.settings.php docroot/sites/default/settings.php; chmod -R 777 docroot/sites/default/settings.php;
        echo "drop database drupal; create database drupal;" | mysql -u root;
        drush si ezcontent --db-url='mysql://root:@127.0.0.1/drupal' --site-name='EZ Content BLT' --account-name='admin' --account-pass='admin' -y;
        drush en ezcontent_demo -y;
        drush en ezcontent_api -y;
        drush cr;'''
      }
    }

  }
}
