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
        stage('Deploy') {
            steps {
                sh 'mvn deploy'
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