pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
                sh 'ls'
                sh 'cd build'
                sh 'ls'
            }
        }
        stage('S3 Upload') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'c29e50f3-e163-4876-81f2-228c36a7e69a') {
                    sh 'ls -la build'
                    sh 'aws s3 cp build s3://jenkins-reactjs/ --recursive'
                }
            }
        }
    }
}
