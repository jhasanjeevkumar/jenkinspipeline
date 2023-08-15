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
          environment{
            LocalVariable = "HelloLocal"
          }
          steps {
            echo 'Testing the application'
            writeFile(file: 'LogTestFile.txt', text: "This is a local variable {LocalVariable}")
          }
        }
        stage('Artifacts'){
              steps{
                echo 'Testing the artifacts'
                archiveArtifacts Artifacts: 'LogTestFile.txt'
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