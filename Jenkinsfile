pipeline {
  environment {
    dockerimagename = "gabryvv/progettone"
    dockerImage = ""
  }
  
  
  
  
  agent {
        docker {
            image 'ubuntu'
            args '-u root:sudo -v $HOME/workspace/myproject:/myproject'
        }
  }
  
  
  
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/gabryvv/progettone-serio'
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
