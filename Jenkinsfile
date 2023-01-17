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

        stage('Build') {
            steps {
                withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v10/') {
                    sh 'docker build -t 20127090/reactapp .'
                    sh 'docker push 20127090/reactapp:latest'
                }
            }
        }

        // stage('Install packages') { 
        //     steps {
        //         sh 'npm install' 
        //     }
        // }

        // stage('Test') { 
        //     steps {
        //         sh 'npm test' 
        //     }
        // }

        // stage("Build") {
        //     agent { dockerfile true }
        //     steps {
                
        //     }
        // }

        // stage('Build') {
        //     agent { dockerfile true }
        //     steps {
        //         withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        //             sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
        //             sh 'docker build -t 20127090/reactapp .'
        //             sh 'docker push 20127090/reactapp:latest'
        //         }
        //     }
        // }
    }
}