pipeline {
    agent any
 
    stages {
 
        stage('Checkout') {
            steps {
                git 'https://github.com/Praveenkannan-2023/devops-poc.git'
            }
        }
 
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                      sonar-scanner
                    '''
                }
            }
        }
 
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-poc .'
            }
        }
 
        stage('Deploy') {
            steps {
                sh 'docker run -d --rm devops-poc'
            }
        }
    }
}
