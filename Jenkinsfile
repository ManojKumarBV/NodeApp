pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Build React App') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }
        stage('Run React App') {
            steps {
                script {
                    sh 'npm start --host 0.0.0.0 --port 4001'
                }
            }
        }
        stage('Deliver') {
            steps {
                input message: 'Finished using the website? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
