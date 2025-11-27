pipeline {
    agent { label 'java' }
    stages { 
        stage('checkout') {
            steps {
               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
            }
        }
        stage('build') {
            steps {
               sh "mvn clean package"
            }
        }
        stage('deploy') {
            steps {
               sh "sudo cp /home/slave1/workspace/helloworld_pipelie/target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.1.49/webapps/"
                
            }
        }
    }
}
