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

    stage('Install Packages') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Build') {
      steps {
        sh 'socker build -t reactapp'
      }
    }

  }
}