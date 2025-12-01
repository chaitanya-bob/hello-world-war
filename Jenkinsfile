pipeline {
    // agent { label 'java' }
    agent none
    parameters {
        string(name: 'mcmd1', defaultValue: 'clean', description: 'maven clean command')
        booleanParam(name: 'SAMPLE_BOOLEAN', defaultValue: true, description: 'A boolean parameter')
        choice(name: 'mcmd2', choices: ['package', 'compile', 'install', 'validate'], description: 'Choose one option')
    }
    stages {
        stage ('hello-world-war') {
            parallel {
                stage('Checkout') {
                    agent { label 'java' }
                    steps {
                        withCredentials([
                            usernamePassword(credentialsId: '2f7204ff-bc30-4049-9653-20116f9567b5',
                                usernameVariable: 'MY_USERNAME',
                                passwordVariable: 'MY_PASSWORD'),
                            sshUserPrivateKey(credentialsId: 'c6744ca3-8f05-4999-b666-fe83b7da220e',
                                keyFileVariable: 'KEY_FILE',
                                usernameVariable: 'SSH_USER')
                        ]) {
                            sh "rm -rf hello-world-war"
                            sh "git clone https://github.com/yashusn/hello-world-war"
                        }
                    }
                }

                stage('Build') {
                    agent { label 'java' }
                    steps {
                        sh "mvn $mcmd1 $mcmd2"
                    }
                }
            }
        }

        stage('Deploy') {
            agent { label 'java' }
            steps {
                sh "sudo cp /home/slave1/workspace/helloworld_pipelie/target/hello-world-war-1.0.1.war /opt/apache-tomcat-10.1.49/webapps"
            }
        }
    }
}
