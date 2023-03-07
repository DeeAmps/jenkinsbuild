pipeline {
    agent {
        docker {
            image 'node:lts-bullseye-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests'
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
            }
        }
    }
}