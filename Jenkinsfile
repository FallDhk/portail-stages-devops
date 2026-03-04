pipeline {
    agent any

    stages {

        stage('Clone Backend') {
            steps {
                dir('backend') {
                    git branch: 'main', url: 'https://github.com/TON_USERNAME/PortailStages.git'
                }
            }
        }

        stage('Clone Frontend') {
            steps {
                dir('frontend') {
                    git branch: 'main', url: 'https://github.com/TON_USERNAME/portail-stages-frontend.git'
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}
