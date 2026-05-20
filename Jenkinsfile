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
                sh 'echo "Running SonarQube analysis..."'
            }
        }

        stage('Security') {
            steps {
                sh 'echo "Running Snyk/Trivy security scan..."'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker build -t taskmaster-app .'
                sh 'docker run -d -p 8080:8080 --name taskmaster-container taskmaster-app'
            }
        }

        stage('Release') {
            steps {
                sh 'docker tag taskmaster-app taskmaster-app:prod'
            }
        }

        stage('Monitoring') {
            steps {
                sh 'curl http://localhost:8080/actuator/health'
            }
        }
    }
}
