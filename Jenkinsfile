pipeline {
    agent any

    stages {
        stage('Prepare') {
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
        stage('Sonarqube Scan') {
            steps {
                sh 'echo StageSkipped'
            }
        }
        stage('Nexus IQ') {
            steps {
                sh 'echo StageSkipped'
            }
        }
         stage('Dockerise') {

            steps {
                sh 'docker build -t goapp:${BUILD_ID}-${BUILD_NUMBER} . && docker run -d ubuntu'
            }
        }
        stage('Docker Bootup Test') {

            steps {
                sh 'docker rm -f $(docker ps -a -q) && docker run -d -p 8070:8080 goapp:${BUILD_ID}-${BUILD_NUMBER}'
            }
        }
        stage('Automation Testing') {

            steps {
                sh 'rm -rf autohack && git clone https://github.com/deenaboopathy/autohack.git && python3 ./autohack/automationscript.py 8070'
            }
        }
        stage('Clean UP') {

            steps {
                sh 'docker rm -f $(docker ps -a -q)'
            }
        }
    }
}
