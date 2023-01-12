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
        withDockerRegistry(credentialsId: 'docker', toolName: 'Docker', url: 'https://index.docker.io/v1/') {
          sh 'docker build -t reactapp .'
          sh 'docker push reactapp .'
        }
      }
    }

  }
}