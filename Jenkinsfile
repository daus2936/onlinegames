pipeline {
    agent any
    tools {
        djk 'jdk17'
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