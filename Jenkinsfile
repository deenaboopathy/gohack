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
                sh '/usr/local/go/bin/go build'
            }
        }

        stage('Test') {
            steps {
                sh '/usr/local/go/bin/go test ./...'
            }
        }
         stage('Dockerise') {
            steps {
                sh 'docker build -t localbuild .'
            }
        }
    }
}
