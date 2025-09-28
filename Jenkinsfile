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
        
        stage('Install & Test') {
            steps {
                sh 'npm install --save'
                sh 'npm test'
            }
        }
        
        stage('Build Docker') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }
    }
}
