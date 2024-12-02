// Jenkinsfile
pipeline {
    agent any // Use any available agent/node
    options {
        timeout(time: 30, unit: 'MINUTES') // Timeout after 30 minutes
    }
    environment {
        // Define environment variables (if needed)
        BUILD_ENV = 'Sandbox'
    }
    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/fhjfong/testJava.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                // sh 'npm install' // Example for a Node.js project
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                // sh 'npm run build' // Replace with your build command
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                // sh 'npm test' // Replace with your test command
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging artifacts...'
                sh 'zip -r build-artifacts.zip build/' // Example: Packaging build artifacts
                archiveArtifacts artifacts: 'build-artifacts.zip', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to environment...'
                // sh './deploy.sh ${BUILD_ENV}' // Example: Deploy script
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
            cleanWs() // Clean up the workspace
        }
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
