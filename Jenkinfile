
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing application files'
                sh 'ls -la'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to Apache'

                sh '''
                    install -m 644 index.html /var/www/html/index.html
                '''
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying deployed application'
                sh 'curl -f http://localhost/'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}

