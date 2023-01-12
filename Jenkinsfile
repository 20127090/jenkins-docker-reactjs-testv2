pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/20127090/jenkins-docker-reactjs-testv2', branch: '*/master')
      }
    }

    stage('Test') {
      steps {
        echo 'Done :)))'
      }
    }

  }
}