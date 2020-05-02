pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''rm -rf ezcontent-install;
rm ~/.composer/cache/repo/https---repo.packagist.org/provider-srijanone\\$ezcontent.json;
rm ~/.composer/cache/repo/https---repo.packagist.org/provider-srijanone\\$ezcontent-project.json;
COMPOSER_MEMORY_LIMIT=-1 php composer.phar create-project srijanone/ezcontent-project:8.x-dev ezcontent-install --no-interaction;
cd ezcontent-install;
echo "Creating required files.";
mkdir -p docroot/sites/default/files; chmod -R 777 docroot/sites/default/files; cp docroot/sites/default/default.settings.php docroot/sites/default/settings.php; chmod -R 777 docroot/sites/default/settings.php;
echo "Drop and create DB.";
echo "drop database ez; create database ez;" | mysql -u root;
echo "Installing EZContent."
drush si ezcontent --db-url=\'mysql://root:@127.0.0.1/ez\' --site-name=\'EZ Content\' --account-name=\'admin\' --account-pass=\'admin\' -y;
drush uli --uri=http://local.ez.com/;'''
      }
    }

  }
}
