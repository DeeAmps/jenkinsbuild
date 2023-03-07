pipeline {
    agent any

    tools {
        nodejs "nodejs"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Installing npm dependencies'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                sh 'npm test'
            }
        }
        
        stage('Building Docker image') {
            steps {
                echo 'Building docker image..'
                sh 'docker build -t deeamps/nodejenkins .'
            }
        }

        stage ('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')], {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push deeamps/nodejenkins'
                })
                
            }
        }
    }
}
