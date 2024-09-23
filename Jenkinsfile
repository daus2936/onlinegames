pipeline {
    agent any
    tools {
        jdk 'jdk17'
        nodejs 'node16'
    }
    environment {
        SCANNER_HOME=tool 'sonar-scanner'
    }
    stages {
        stage('Clean the workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout the project from github repo') {
            steps {
                git branch: 'main', url: 'git@github.com:daus2936/onlinegames.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        stage('Docker Build using the Dockerfile and then push it to DockerHub') {
            steps {
               script {
                   withDockerRegistry(credentialsId: 'daus2936-docker', toolName: 'docker') {
                   sh "docker build -t bingoonlproject . "
                   sh "docker tag bingoonlproject daus2936/bingoonlproject:latest"
                   sh "docker push daus2936/bingoonlproject:latest "
                 }
               }
            }
        }
    }
}