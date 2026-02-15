pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
                echo "Building branch: ${env.BRANCH_NAME}"
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Train Reservation System...'
                // Add your build commands here later
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here later
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment commands here later
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
