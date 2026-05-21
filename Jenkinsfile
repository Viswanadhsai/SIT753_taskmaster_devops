pipeline {
    agent any

    stages {

        stage('Build & Test') {
            parallel {
                stage('Build') {
                    steps {
                        echo "Building with Maven..."
                        sh 'mvn clean package -DskipTests'
                    }
                }
                stage('Test') {
                    steps {
                        echo "Running tests..."
                        sh 'mvn test'
                    }
                }
            }
        }

        stage('Quality Gates') {
            parallel {
                stage('Code Quality') {
                    steps {
                        echo "Running code quality checks..."
                        sh 'mvn verify'
                    }
                }
                stage('Security Scan') {
                    steps {
                        echo "Running security scan..."
                        sh 'mvn org.owasp:dependency-check-maven:check'
                    }
                }
            }
        }

        stage('Docker Build & Run') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t myapp:latest .'

                echo "Running Docker container..."
                sh 'docker run --rm myapp:latest'
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
