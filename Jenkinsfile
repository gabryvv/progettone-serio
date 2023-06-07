pipeline {
  environment {
    dockerimagename = "gabryvv/progettone"
    dockerImage = ""
  }
  
  
  
  
  agent {
    docker { image 'node:18.16.0-alpine' }
  }
  
  
  
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/gabryvv/progettone-serio'
      }
    }
    
   

     stage("installazione docker sul nodo") {
            steps {
                sh 'apt install docker'
                sh 'echo docker -v'
            }
        }
    
    
    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhub-credentials'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com/', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
    }
  }
}
