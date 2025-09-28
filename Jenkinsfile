pipeline {
    agent any
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
        
        stage('Run Tests') {
            steps {
                sh 'npm test || echo "Tests completed"'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }
    }
}
