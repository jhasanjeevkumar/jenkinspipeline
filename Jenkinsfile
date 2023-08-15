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
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying the code to server'
      }
    }
    stage('Artifacts'){
      steps{
         echo 'Testing the artifacts'
           archiveArtifacts 'LogTestFile.txt'
          }
    }
    stage("Interactive_Input") {
            steps {
                script {

                    // Variables for input
                    def inputConfig
                    def inputTest

                    // Get the input
                    def userInput = input(
                            id: 'userInput', message: 'Enter path of test reports:?',
                            parameters: [

                                    string(defaultValue: 'None',
                                            description: 'Path of config file',
                                            name: 'Config'),
                                    string(defaultValue: 'None',
                                            description: 'Test Info file',
                                            name: 'Test'),
                            ])

                    // Save to variables. Default to empty string if not found.
                    inputConfig = userInput.Config?:''
                    inputTest = userInput.Test?:''

                    // Echo to console
                    echo("IQA Sheet Path: ${inputConfig}")
                    echo("Test Info file path: ${inputTest}")

                    // Write to file
                    writeFile file: "inputData.txt", text: "Config=${inputConfig}\r\nTest=${inputTest}"

                    // Archive the file (or whatever you want to do with it)
                    archiveArtifacts 'inputData.txt'
                }
            }
        }
  }
      environment {
    jenkinspath = 'C:\\Users\\sanjeev\\jenkinsdata'
  }

}