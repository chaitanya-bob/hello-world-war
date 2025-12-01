pipeline {
  //  agent { label 'java' }
      agent none
   parameters {
string(name: 'cmd', defaultValue: 'default', description: 'A sample string parameter')
booleanParam(name: 'SAMPLE_BOOLEAN', defaultValue: true, description: 'A boolean parameter')
choice(name: 'cmd1', choices: ['install', 'compile'], description: 'Choose one option')
}

    stages { 
        stage ('hello-world-war') {
            parallel {
        stage('checkout') {
            agent { label 'java' }
            steps {
                withCredentials([usernamePassword(
                            credentialsId: '53798f27-0ed8-4bc5-84df-9e6c23bc5b73',
                            usernameVariable: 'chaitanya',
                            passwordVariable: '1234'
                     /*  withCredentials([sshUserPrivateKey(
                            credentialsId: '3f6a9c95-2ecd-4bbe-a817-1ab975fb98d3',
                             keyFileVariable: 'chaitanya_SSH_KEY',
                             usernameVariable: 'chaitanya_SSH_USER' */
                        )]) {

               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
            }
        }
        stage('build') {
            agent { label 'java' }
            steps {
               sh "mvn clean package"
            }
        }
        stage('deploy') {
            agent { label 'java' }
            steps {
               sh "sudo cp /home/slave1/workspace/helloworld_pipelie/target/hello-world-war-1.0.1.war /opt/apache-tomcat-10.1.49/webapps/"
                
            }
        }
        }        
    }
}
}
