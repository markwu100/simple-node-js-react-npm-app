pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'sudo npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'sudo ./jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh 'sudo ./jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'sudo ./jenkins/scripts/kill.sh'
            }
        }
    }
}
