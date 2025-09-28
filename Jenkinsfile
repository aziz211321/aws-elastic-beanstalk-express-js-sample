pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root:root'
        }
    }
    environment {
        DOCKER_IMAGE = 'abdulaziz2009/my-node-app'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aziz211321/aws-elastic-beanstalk-express-js-sample.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                sh 'npm test'
            }
        }
        
        stage('Security Scan') {
            steps {
                sh 'npm install -g snyk'
                sh 'snyk test --severity-threshold=high || true'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("my-node-app:${env.BUILD_ID}")
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed. Check logs for details.'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
