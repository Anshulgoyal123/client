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
                sh '''docker build -t myapp .
                docker run -p 9090:9090 --name myjavaapp myapp'''
            }
        }
    }
}
