pipeline {
environment {
dockerimagename = "gabryv/progettone"
dockerImage = ""
}

agent any

stages {

stage('Checkout Source') {
steps {
container('docker') {
git branch: 'main', credentialsId: 'github-credentials', url: 'git@github.com:gabryvv/progettone-serio.git'
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


}

}
