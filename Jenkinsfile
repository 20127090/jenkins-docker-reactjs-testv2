pipeline {
  agent {
        docker {
            image 'node:lts-bullseye-slim' 
            args '-p 3000:3000' 
        }
    }
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/20127090/jenkins-docker-reactjs-testv2.git'
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