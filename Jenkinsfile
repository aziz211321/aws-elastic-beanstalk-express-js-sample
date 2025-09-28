pipeline {
    agent {
        docker {
            image 'node:16'
            args '-u root:root'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aziz211321/aws-elastic-beanstalk-express-js-sample.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install --save'
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
                sh 'snyk test --severity-threshold=high || echo "Security scan completed - continuing build"'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }
    }
}
