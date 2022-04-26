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
                dir('DotnetTemplate.Web'){
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm t'
                    sh 'npm run lint'
                }
            }  
        }
    }
}