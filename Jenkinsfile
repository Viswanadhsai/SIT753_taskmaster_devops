pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Building application..."
                sh 'sleep 2'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'sleep 2'
            }
        }

        stage('Code Quality') {
            steps {
                echo "Checking code quality..."
                sh 'sleep 2'
            }
        }

        stage('Security') {
            steps {
                echo "Running security scan..."
                sh 'sleep 2'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh 'sleep 2'
            }
        }

        stage('Release') {
            steps {
                echo "Release completed..."
                sh 'sleep 2'
            }
        }

        stage('Monitoring') {
            steps {
                echo "Monitoring application..."
                sh 'sleep 2'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
