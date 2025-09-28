pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aziz211321/aws-elastic-beanstalk-express-js-sample.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install --save'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'npm audit || true'
                sh 'echo "Security scan: OWASP Dependency Check would run here"'
            }
        }
        stage('Validate Docker') {
            steps {
                sh 'cat Dockerfile | grep "node:16" && echo "✅ Node 16 verified in Dockerfile"'
            }
        }
    }
}
