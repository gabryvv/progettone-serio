/*pipeline {
environment {
dockerimagename = "gabryv/progettone"
dockerImage = ""
}

*/
pipeline{
agent any

/*
stages {

stage('Checkout Source') {
steps {
container('docker') {
git branch: 'main', credentialsId: 'github-credentials', url: 'git@github.com:gabryvv/progettone-serio.git'
}
}
}*/

    stages {
        stage("Clone Git Repository") {
            steps {
                git(
                    url: "git@github.com:gabryvv/progettone-serio.git",
                    branch: "main",
                    changelog: true,
                    poll: true
                )
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