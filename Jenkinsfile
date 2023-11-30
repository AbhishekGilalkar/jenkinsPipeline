
pipeline {
    agent any
    stages {
        stage('Build app') {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/AbhishekGilalkar/jenkinsPipeline.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t jenkinsdockers .'
                }
            }
        }

        stage('Rename Image Tag') {
            steps {
                script {
                    bat 'docker tag jenkinsdockers immortal650/jenkinsdockerapp1:image1'
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                script {
                    bat 'docker login -u immortal650 -p exide_@123'
                    bat 'docker push immortal650/jenkinsdockerapp1:image1'
                }
            }
        }
    }
}
