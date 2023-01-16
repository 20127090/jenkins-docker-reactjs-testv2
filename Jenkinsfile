pipeline {
    agent {
        docker {
            image 'node'
            args '-p 3000:3000'
        }
    }

    stages {
        stage('Install packages') { 
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
                withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/') {
                sh 'docker build -t reactapp .'
                sh 'docker push reactapp .'
                }
            }
        }
    }
}