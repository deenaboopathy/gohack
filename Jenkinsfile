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
