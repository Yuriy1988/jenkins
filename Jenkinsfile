pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'chmod -R 777 ./jenkins/scripts'
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
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/**/*', fingerprint: true
        }
    }
}