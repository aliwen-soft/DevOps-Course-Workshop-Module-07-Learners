pipeline {
    agent none

    stages {
        stage('Build and test C sharp') {
            steps {
                echo 'cSharp..'
            }
        }
        stage('Build and test Ts') {
            agent {
                docker {
                    image 'node:17-bullseye'
                }
            }
            steps {
                sh 'npm install'
                sh 'npm run build'
                sh 'npm t'
            }
        }
    }
}