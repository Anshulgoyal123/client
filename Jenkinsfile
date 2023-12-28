pipeline {
    agent any

    stages {
        // stage('Hello') {
        //     steps {
        //         git 'https://github.com/Anshulgoyal123/client.git'
        //     }
        // }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Containerized the application') {
            steps {
                sh '''docker build -t timesheetapp:${BUILD_ID} .
                
                docker run -d -p 9090:9090 --name timesheetapplication${BUILD_ID} timesheetapp:${BUILD_ID}
                docker commit timesheetapplication${BUILD_ID} timesheetfinalapp${BUILD_ID} 
                docker tag timesheetfinalapp${BUILD_ID} 9639287812/timesheetapplication:${BUILD_ID} 
                docker push 9639287812/timesheetapplication:${BUILD_ID} '''
            }
        }
        stage('sonar analysis') {
            steps {
            withSonarQubeEnv('sonarqube-9.9.3') {
                sh "mvn sonar:sonar"
            }
            }
        }
    }
}
