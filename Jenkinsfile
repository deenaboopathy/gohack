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
         stage('Dockerise') {
            steps {
                sh 'docker build -t goapp:${BUILD_NUMBER} .'
            }
        }
        stage('Docker Bootup Test') {
            steps {
                sh 'docker rm -f $(docker ps -a -q) && docker run -d -p 8070:8080 goapp:${BUILD_NUMBER}'
            }
        }
        stage('Automation Testing') {
            steps {
                sh 'git clone https://github.com/deenaboopathy/autohack.git && cd autohack && python3 automationscript.py'
            }
        }
        stage('Clean UP') {
            steps {
                sh 'docker rm -f $(docker ps -a -q)'
            }
        }
    }
}
