pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''COMPOSER_MEMORY_LIMIT=-1 composer create-project srijanone/ezcontent-project:8.x-dev ezcontent-install --no-interaction;'''
      }
    }

  }
}
