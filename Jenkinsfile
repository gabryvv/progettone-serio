pipeline {
environment {
dockerimagename = "gabryv/progettone"
dockerImage = ""
}

agent
  {
  docker { image 'node:18.16.0-alpine' }
  }

stages {

stage('Checkout Source') {
 steps {
        git branch: 'main', credentialsId: 'github-credential', url: 'https://github.com/gabryvv/progettone-serio.git'
      }
}

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
}
}