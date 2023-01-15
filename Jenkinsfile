// pipeline {
//   agent {
//         docker {
//             image 'node:lts-bullseye-slim' 
//             args '-p 3000:3000' 
//         }
//     }

//   }
//   stages {
//     stage('Clone') {
//       steps {
//         git 'https://github.com/20127090/jenkins-docker-reactjs-testv2'
//       }
//     }

//     stage('Install Packages') {
//       steps {
//         sh 'npm install'
//       }
//     }

//     stage('Test') {
//       steps {
//         sh 'npm test'
//       }
//     }

//     stage('Build') {
//       steps {
//         withDockerRegistry(credentialsId: 'docker', url: 'https://index.docker.io/v1/') {
//           sh 'docker build -t reactapp .'
//           sh 'docker push reactapp .'
//         }
//       }
//     }

//   }
agent {
        docker {
            image 'node:lts-bullseye-slim' 
            args '-p 3000:3000' 
        }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
    }