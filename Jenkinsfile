pipeline {
    agent any
    stages {
        stage('Download') {
            steps {
                echo "Download Code from Github"
                git branch: 'main', url: 'https://github.com/bheesham-devops/maven-jenkins10.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Build the application docker image and push to Docker Hub"
                sh '''docker build -t bheeshamdevops/java-webapp:v${BUILD_NUMBER} .
                docker tag bheeshamdevops/java-webapp:v${BUILD_NUMBER} bheeshamdevops/java-webapp:latest
                docker push bheeshamdevops/java-webapp:v${BUILD_NUMBER}
                docker push bheeshamdevops/java-webapp:latest
                '''
            }
        }
    }
}
