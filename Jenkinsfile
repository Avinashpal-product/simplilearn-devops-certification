pipeline {
  environment {
    registry = "avinashpal/simplilearn-devops-certification"
    registryCredential = 'a124bff3-43f2-45a9-95d1-06a883f0208d'
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

