pipeline {
  agent any
  stages {
    stage('clone') {
      steps {
        sh 'git clone https://github.com/Anshulgoyal123/client.git'
      }
    }

    stage('build') {
      steps {
        sh 'mvn clean'
      }
    }

  }
}