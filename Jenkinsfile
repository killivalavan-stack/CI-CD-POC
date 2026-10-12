
pipeline {
    agent any

    stages {
        stage('Test NodeJS') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS-24') {
                    sh 'node --version'
                    sh 'npm --version'
                }
            }
        }
    }
}
