pipeline {
    agent any
    tools {
        jdk 'jdk17'
        nodejs 'node16'
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
    }
}