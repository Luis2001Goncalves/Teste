pipeline {
    agent { label 'Built-In Node' }
    stages {
        stage('Debugging') {
            steps {
                echo 'Starting debugging...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                script {
                    sh 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                script {
                    sh 'npm test'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                script {
                    docker.build("minha-app:${env.BUILD_ID}")
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                echo 'Deploying to Kubernetes...'
                script {
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
}
