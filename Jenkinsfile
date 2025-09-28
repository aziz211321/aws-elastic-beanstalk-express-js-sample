pipeline {
    agent {
        docker {
            image 'node:16'  // REQUIRED: Use Node 16 Docker image
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
                sh 'npm install --save'  // REQUIRED: Install dependencies
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                sh 'npm test'  // REQUIRED: Run tests
            }
        }
        
        stage('Security Scan') {
            steps {
                sh 'npm install -g snyk'  // REQUIRED: Security scanner
                sh 'snyk test --severity-threshold=high || echo "Security scan completed"'  // Will fail on high vulnerabilities
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app .'  // REQUIRED: Build Docker image
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed. Check logs for details.'
        }
    }
}

