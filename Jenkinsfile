pipeline {

    agent any

    stages {

        stage('Clone Source Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Package Application') {
            steps {
                sh 'tar -czf cartforge-app.tar.gz dist/'
            }
        }

        stage('Deliver Artifact') {
            steps {
                archiveArtifacts artifacts: 'cartforge-app.tar.gz', fingerprint: true
            }
        }
    }
}
