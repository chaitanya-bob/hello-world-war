pipeline {
    agent { label 'java' }
    
    stages { 
        stage('Checkout') {
            steps {
               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
            }
        }
        stage('Build') {
            steps {
               sh "mvn clean package"
            }
        }
        stage('Deploy') {
            steps {
               sh "sudo cp /var/lib/jenkins/workspace/helloworld_pipelie/target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.1.49/webapps/"
             
            
            }
        }
    }
}
