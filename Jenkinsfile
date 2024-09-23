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
    }
}