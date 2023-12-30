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
                sh ''' docker run -it -p 9090:9090 --name timesheetapplication${BUILD_ID} 9639287812/timesheet:timesheet
                service mysql start '''
            }
        }
        // stage('sonar analysis') {
        //     steps {
        //     withSonarQubeEnv('sonarqube-9.9.3') {
        //         sh "mvn sonar:sonar"
            // }
            // }ignore
        // }
    }
}
