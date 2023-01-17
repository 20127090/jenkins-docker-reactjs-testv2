pipeline {
    agent {
        docker {
            image 'node'
            args '-p 3000:3000'
        }
    }

    environment {
        registry = "20127090/reactapp"
        registryCredential = "docker"
    }

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'Git', url: 'https://github.com/20127090/jenkins-docker-reactjs-testv2.git'
            }
        }

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
            agent { dockerfile true }
            steps {
                // withDockerRegistry([credentialsId: 'docker', url: 'https://index.docker.io/v1/']) {
                    
                // }
                docker.build registry
            }
        }
    }
}