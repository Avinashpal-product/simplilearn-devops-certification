pipeline {
  environment {
    registry = "avinashpal/simplilearn-devops-certification"
    registryCredential = 'dockerhub'
  }
  agent any
  stages {
        stage('Building image') {
        steps{
            script {
            dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
        }
        }
   }   
}

