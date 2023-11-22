pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Setup') {
            steps {
                sh 'export PATH=$PATH:/usr/local/go/bin'
            }
        }

        stage('Build') {
            steps {
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
