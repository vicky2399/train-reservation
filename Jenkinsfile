pipeline {
    agent any
    
    tools {
    maven 'Maven3'
}

    
    environment {
        MAVEN_OPTS = '-Dmaven.test.failure.ignore=true'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out Train Reservation System from GitHub...'
                echo "Building branch: ${env.BRANCH_NAME}"
                echo "Build number: ${env.BUILD_NUMBER}"
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building Train Reservation System with Maven...'
                sh 'mvn clean compile'
                echo 'Java compilation completed successfully!'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running Maven tests...'
                sh 'mvn test'
                echo 'Tests completed!'
            }
            post {
                always {
                    // Publish test results if they exist
                    publishTestResults testResultsPattern: 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Package') {
            steps {
                echo 'Packaging Train Reservation WAR file...'
                sh 'mvn package'
                echo 'WAR file created successfully!'
            }
            post {
                success {
                    // Archive the WAR file
                    archiveArtifacts artifacts: 'target/*.war', fingerprint: true
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying Train Reservation System...'
                echo 'WAR file ready for deployment to Tomcat server'
                // Add actual deployment commands here later
                sh 'ls -la target/'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Train Reservation Pipeline completed successfully!'
            echo 'WAR file is ready for deployment!'
        }
        failure {
            echo '❌ Pipeline failed! Check the logs above.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
