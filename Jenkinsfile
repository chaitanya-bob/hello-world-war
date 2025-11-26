pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
            }
        }
    }
}
