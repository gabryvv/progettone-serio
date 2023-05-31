pipeline {
environment {
dockerimagename = "gabryv/progettone"
dockerImage = ""
}

agent
  {
  dockerfile true
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