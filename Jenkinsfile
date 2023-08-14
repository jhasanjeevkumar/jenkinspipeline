pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building the first pipeline'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
          }
        }

        stage('Deploy') {
          steps {
            echo 'Deploying the app in OS'
          }
        }

      }
    }

  }
}