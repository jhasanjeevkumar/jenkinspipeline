pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo '"Building the first pipeline with ${jenkinspath}"'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the code to server'
      }
    }

  }
  environment {
    jenkinspath = 'C:\\Users\\sanjeev\\jenkinsdata'
  }
}