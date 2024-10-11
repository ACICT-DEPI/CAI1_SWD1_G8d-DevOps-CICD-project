pipeline {
    agent any

    environment {
        DOCKER_HUB_REPO = 'mohamed907/depi-flask-app'  // Your Docker Hub repository
        GIT_REPO_URL = 'https://github.com/mohamedsamir907/depi-project-aws.git'  // Your public GitHub repository URL
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: "${env.GIT_REPO_URL}"
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Specify the path to the Dockerfile inside the app folder
                    dockerImage = docker.build("${env.DOCKER_HUB_REPO}:${env.BUILD_NUMBER}", "app/")
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    dockerImage.push()
                }
            }
        }
    }

    post {
        always {
            cleanWs()  // Clean workspace after build
        }
    }
}
