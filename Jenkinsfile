pipeline {
    agent any
    stages { 
        stage('installmaven ') {
            steps {
               sh "sudo apt update -y"
               sh "sudo apt install maven -y"
            }
        }
        stage('checkout') {
            steps {
               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
            }
        }
    }
}
