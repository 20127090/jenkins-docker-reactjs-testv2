pipeline {
  agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
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

    stage("Build") {
      steps {
        sh 'socker build -t reactapp'
      }
    }

  }
}