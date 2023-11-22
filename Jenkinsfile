pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'export PATH=$PATH:/usr/local/go/bin'
                sh 'go build'
            }
        }

        stage('Test') {
            steps {
                sh 'go test ./...'
            }
        }
    }
}
