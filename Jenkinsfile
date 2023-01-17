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

        stage("Build") {
            agent { dockerfile true }
            steps {
                sh 'docker build -t 20127090/reactapp .'
            }
        }

        // stage('Build') {
        //     agent { dockerfile true }
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        //             sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
        //             sh "docker "
        //             sh 'docker push shanem/spring-petclinic:latest'
        //         }
        //     }
        // }
    }
}