pipeline {
environment {
dockerimagename = "gabryv/progettone"
dockerImage = ""
}

agent {
}

stages {

stage('Checkout Source') {
steps {
container('docker') {
git branch: 'main', credentialsId: 'github-credentials', url: 'https://github.com/gabryvv/PROGETTONE.git'
}
}
}

stage('Build image') {
steps{
container('docker') {
script {
sh 'docker build -t gabryv/progettone .'
}
}
}
}

stage('Login-Docker') {
steps {
container('docker') {
sh 'docker login -u <docker_username> -p <docker_password>'
}
}
}

stage('Push-Images-Docker-to-DockerHub') {
steps {
container('docker') {
sh 'docker push gabryv/progettone:latest'
}
}
}


stage('Deploying React.js container to Kubernetes') {
steps {
script {
kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
}
}
}

}

}
