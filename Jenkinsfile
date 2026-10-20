pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git(
                    branch: 'main',
                    url: 'https://github.com/SalahAA8/api_testing_project.git'
                )
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('API Tests') {
            steps {
                sh 'mvn -B test'
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
            testResults: '**/target/surefire-reports/*.xml'
        }
    }
}

