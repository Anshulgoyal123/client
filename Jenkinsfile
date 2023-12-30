pipeline {
    agent any

    stages {
        // stage('Hello') {
        //     steps {
        //         git 'https://github.com/Anshulgoyal123/client.git'
        //     }
        // }
        // stage('Build') {
        //     steps {
        //         sh 'mvn clean install'
        //     }
        // }
        stage('Containerized the application') {
            steps {
                sh ''' docker rm -f ${docker ps -qa} 
                docker run -dit -p 9090:9090 --name timesheetapplication${BUILD_ID} 9639287812/timesheet:timesheetimage
                docker exec -it timesheetapplication${BUILD_ID} 
                service mysql start
                cd /pro/client/target
                java -jar timesheet-0.0.1-SNAPSHOT.jar  --spring.config.location=/pro/client/src/main/resources/application.properties '''
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
