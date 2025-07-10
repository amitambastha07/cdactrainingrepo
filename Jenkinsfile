pipeline {
    agent any

    environment {
        // WARNING: Hardcoding secrets is insecure!
        GIT_USER = 'amitambastha07'
        GIT_TOKEN = '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'
        GIT_URL = 'https://github.com/amitambastha07/cdactrainingrepo.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone using the token (for demonstration only)
                sh 'git clone https://${GIT_USER}:${GIT_TOKEN}@github.com/amitambastha07/cdactrainingrepo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("my-app:latest")
                }
            }
        }

        stage('Docker Image Check') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'ls -l /app/my-binary || exit 1'
                        // You can add more checks or tests here
                    }
                }
            }
        }
    }
}
