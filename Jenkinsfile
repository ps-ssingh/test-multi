pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Checking  code...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing project...'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            when {
                branch 'main' // Specifies that deployment should occur only from the main branch
            }
            steps {
                echo 'Deploying to production...'
                // Add deployment script here
            }
        }
    }
    post {
        always {
            echo 'Sending email notification...'
            // Add mail step here
        }
        success {
            echo 'Build was successful!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
