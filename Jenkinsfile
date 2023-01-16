pipeline {
    agent {
        docker {
            image 'node'
            args '-p 3000:3000'
        }
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
            steps {
                // withDockerRegistry(credentialsId: 'docker', url:'') {
                //     sh "ls"
                //     sh 'docker build -t reactapp .'
                //     sh 'docker push reactapp .'
                // }
                sh "docker build -t reactapp ."
                sh 'docker push reactapp .'
            }
        }
    }
}