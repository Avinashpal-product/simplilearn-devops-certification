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

        stage('Deploy Image') {
        steps{
            script {
            docker.withRegistry( '', 'a124bff3-43f2-45a9-95d1-06a883f0208d' ) {
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
