pipeline {
    agent {
        docker {
            image 'node:18.18.2-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    environment {
        CREDENTIAL_JENKINS = credentials('api-key-aws')
    }
    stages {
        stage('Build') { 
            steps {
                sh 'echo Stage Build is working'
                sh 'echo Test Credential Plugin is $CREDENTIAL_JENKINS'
                sh 'npm install' 
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
             steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
             }
        }
    }
}