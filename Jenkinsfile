pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t employee-management .'
            }
        }

        stage('Docker Deploy') {
            steps {
                bat 'docker rm -f employee-management || exit 0'
                bat 'docker run -d -p 8081:8080 --name employee-management employee-management'
            }
        }
    }
}