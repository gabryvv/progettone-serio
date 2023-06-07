pipeline {
  environment {
    dockerimagename = "gabryvv/progettone"
    dockerImage = ""
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/gabryvv/progettone-serio'
      }
    }
    
    stage('installa docker sul nodo? forse') {
      steps {
        sh '''
            #!/bin/bash
            apt update
            apt install yum
            yum install docker
            echo "docker installato sium"
         '''
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
