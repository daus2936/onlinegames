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
        stage('Sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonarqube-server') {
                    sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.projectKey=BingoOnlineProject \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://18.136.183.0:9000 \
                    -Dsonar.token=sqp_6981582190c46f6243eafc33d1d1340aaf6aed8f
                    '''
                }
            }
        }
        stage('Quality Gate Check') {
            steps {
                waitForQualityGate abortPipeline: false, credentialsId: 'Sonar-token'
            }
        }
    }
}