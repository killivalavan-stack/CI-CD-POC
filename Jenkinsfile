
pipeline {
    agent any

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Node.js') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS-24') {
                    sh 'node --version'
                    sh 'npm --version'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS-24') {
                    sh 'npm ci'
                }
            }
        }

        stage('Build Next.js') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS-24') {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Next.js build completed.'
        }

        failure {
            echo 'FAILURE: Check the Jenkins console output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
