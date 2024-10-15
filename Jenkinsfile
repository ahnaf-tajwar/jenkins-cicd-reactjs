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
                withAWS(region: 'us-east-1', credentials: '4d458c85-a2ba-48c2-9f69-5b29da310a1c') {
                    sh 'ls -la build'
                    sh 'aws s3 cp build s3://jenkins-reactjs/ --recursive'
                }
            }
        }
    }
}
