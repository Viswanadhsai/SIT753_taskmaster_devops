pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                dir('demo/demo') {
                    sh './mvnw clean package -DskipTests'
                }
            }
        }

        stage('Test') {
            steps {
                dir('demo/demo') {
                    sh './mvnw test'
                }
            }
        }

        stage('Code Quality') {
            steps {
                dir('demo/demo') {
                    sh './mvnw checkstyle:check'
                }
            }
        }

        stage('Security') {
            steps {
                dir('demo/demo') {
                    sh './mvnw dependency-check:check'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to local/test environment...'
                sh 'sleep 3'
            }
        }

        stage('Release') {
            steps {
                echo 'Promoting build to release version...'
                sh 'sleep 2'
            }
        }

        stage('Monitoring') {
            steps {
                echo 'Checking application health...'
                sh 'curl -s http://localhost:8080/actuator/health || true'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
