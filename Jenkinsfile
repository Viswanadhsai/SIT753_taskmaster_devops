pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests=false'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Code Quality') {
            steps {
                echo "Running SonarQube analysis..."
            }
        }

        stage('Security') {
            steps {
                echo "Running Snyk/Trivy security scan..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Mock deploy: Building Docker image..."
                echo "Mock deploy: Running container..."
            }
        }

        stage('Release') {
            steps {
                echo "Mock release: Tagging image for production..."
            }
        }

        stage('Monitoring') {
            steps {
                echo "Mock monitoring: Checking application health..."
            }
        }
    }
}
