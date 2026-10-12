 
pipeline {
    agent any

     triggers {
        githubPush()
     }
    tools {
        nodejs 'NodeJS-24'
    }

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

        stage('Check Node and npm') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Build Next.js') {
            steps {
                sh 'npm run build'
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
