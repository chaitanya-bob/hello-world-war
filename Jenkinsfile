pipeline {
  //  agent { label 'java' }
      agent none
   parameters {
string(name: 'mcd1', defaultValue: 'clean', description: 'maven clean command')
        booleanParam(name: 'Boolean', defaultValue: true, description: 'Enable or disable')
        choice(name: 'mcd2', choices: ['install', 'package', 'compile'], description: 'select the choice')

}

    stages { 
        stage ('hello-world-war') {
            parallel {
        stage('checkout') {
            agent { label 'java' }
            steps {
                      withCredentials([usernamePassword(
                           credentialsId: '2f7204ff-bc30-4049-9653-20116f9567b5',
                            usernameVariable: 'chaitanya_user',
                            passwordVariable: 'chaitanya_pass'
                    /*   withCredentials([sshUserPrivateKey(
                            credentialsId: 'c6744ca3-8f05-4999-b666-fe83b7da220e',
                             keyFileVariable: 'chaitanya_SSH_KEY',
                             usernameVariable: 'chaitanya_SSH_USER' */
                        )]) {

               sh "rm -rf hello-world-war"
               sh "git clone https://github.com/chaitanya-bob/hello-world-war"
             }
            }
        }
        stage('build') {
            agent { label 'java' }
            steps {
               sh "mvn $cmd $cmd1"
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
