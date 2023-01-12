pipeline {
  agent {
    dockerfile {
      filename 'Dockerfile'
    }

  }
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/20127090/jenkins-docker-reactjs-testv2'
      }
    }

    stage('Test') {
      steps {
        echo 'Done :)))'
      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

  }
}