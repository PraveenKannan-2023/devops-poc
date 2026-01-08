pipeline {
    agent any
 
    tools {
        sonarScanner 'SonarScanner'
    }
 
    stages {
 
        stage('Checkout') {
            steps {
                git 'https://github.com/PraveenKannan-2023/devops-poc.git'
            }
        }
 
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                      sonar-scanner \
                      -Dsonar.projectKey=devops-poc \
                      -Dsonar.projectName=devops-poc \
                      -Dsonar.sources=.
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
                sh 'docker run -d --name devops-poc-container devops-poc || true'
            }
        }
    }
}
