pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app/demo maven:3.9.6-eclipse-temurin-17 mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app/demo maven:3.9.6-eclipse-temurin-17 mvn test'
            }
        }

        stage('Code Quality') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app/demo maven:3.9.6-eclipse-temurin-17 mvn checkstyle:check || true'
            }
        }

        stage('Security') {
            steps {
                sh 'docker run --rm -v $PWD:/app -w /app/demo maven:3.9.6-eclipse-temurin-17 mvn dependency-check:check || true'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh 'sleep 3'
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
                sh 'echo "Health check simulated"'
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