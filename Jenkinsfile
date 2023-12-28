pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                git 'https://github.com/Anshulgoyal123/client.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Containerized the application') {
            steps {
                sh '''docker build -t myapp:{BUILD_ID} .
                docker run -d -p 9090:9090 --name myjavaapp:${BUILD_ID} myapp:{BUILD_ID}'''
            }
        }
    }
}
