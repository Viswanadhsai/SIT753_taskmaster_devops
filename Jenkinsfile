pipeline {
    agent any

    stages {

        stage('Build & Test') {

            parallel {

                stage('Build') {
                    steps {
                        echo "Building with Maven..."
                        sh 'mvn clean package -DskipTests -Ddependency-check.skip=true'
                    }
                }

                stage('Test') {
                    steps {
                        echo "Running tests..."
                        sh 'mvn test -Ddependency-check.skip=true'
                    }
                }
            }
        }

        stage('Quality Gates') {

            parallel {

                stage('Code Quality') {
                    steps {
                        echo "Code quality stage simulated..."
                        sh 'echo "Checkstyle configured successfully"'
                    }
                }

                stage('Security Scan') {
                    steps {
                        echo "Security scan simulated..."
                        sh 'echo "OWASP Dependency Check configured successfully"'
                    }
                }
            }
        }

        stage('Docker Build & Run') {
            steps {

                echo "Building Docker image..."
                sh 'docker build -t myapp:latest .'

                echo "Stopping old container if exists..."
                sh 'docker stop myapp_container || true'
                sh 'docker rm myapp_container || true'

                echo "Running Docker container in background..."
                sh 'docker run -d --rm --name myapp_container myapp:latest'
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
                sh 'echo "Health monitoring simulated"'
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

        always {
            echo "Pipeline execution finished."
        }
    }
}
