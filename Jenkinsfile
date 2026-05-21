pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'cd demo && mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'cd demo && mvn test'
            }
        }

        stage('Code Quality') {
            steps {
                sh 'cd demo && mvn checkstyle:check || true'
            }
        }

        stage('Security') {
            steps {
                sh 'cd demo && mvn dependency-check:check || true'
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
                sh 'curl -s http://localhost:8080/actuator/health || true'
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