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

        // stage("Build") {
        //     agent { dockerfile true }
        //     steps {
                
        //     }
        // }

        stage('Build') {
            agent { dockerfile true }
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker build -t 20127090/reactapp .'
                    sh 'docker push shanem/spring-petclinic:latest'
                }
            }
            // node {
            //     checkout scm

            //     docker.withRegistry('https://registry.example.com', 'credentials-id') {

            //         def customImage = docker.build("my-image:${env.BUILD_ID}")

            //         /* Push the container to the custom Registry */
            //         customImage.push()
            //     }
            // }
        }
    }
}