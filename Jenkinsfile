pipeline {
  environment {
    registry = "https://hub.docker.com/"
    registryCredential = 'avinashpal-dockerhub'
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

        stage('Deploy Image') {
        steps{
            script {
            docker.withRegistry( '', 'avinashpal-dockerhub' ) {
                dockerImage.push()
            }
            }
        }
        }

        stage('Remove Image') {
        steps{
            sh "docker rmi $registry:$BUILD_NUMBER"
        }
        }
   }   
}

node {
    stage('Execute Image'){
        def customImage = docker.build("avinashpal/simplilearn-devops-certification:${env.BUILD_NUMBER}")
        customImage.inside {
            sh 'echo This is the code executing inside the container.'
        }
    }
}
