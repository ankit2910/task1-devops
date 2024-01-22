pipeline {
    agent any
    // tools {
    //     maven "MAVEN"
    //     jdk "JDK"
    // }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy - Staging') {
            steps {
                sh './deploy staging'
                sh './run-smoke-tests'
            }
        }
        stage('Deploy - Production') {
            steps {
                sh './deploy production'
            }
        }
    }
    post {
        always {
            junit(
                allowEmptyResults: true,
                testResults: '*/test-reports/.xml'
            )
        }
    }
}