pipeline {
    agent {
        docker {
            image 'node:18.18.2-alpine3.18' 
            args '-v /var/run/docker.sock:/var/run/docker.sock -p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}