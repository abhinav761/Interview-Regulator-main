pipeline {
    agent any

    environment {
        // Defines the name of your container image
        IMAGE_NAME = "interview-regulator-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Fetches the code from your repository
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                // Using 'bat' since you are running Jenkins on Windows.
                // If you ever move Jenkins to Linux, swap 'bat' for 'sh'.
                bat "docker build -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Deploy Locally') {
            steps {
                script {
                    // Try to stop and remove any existing container first to avoid port conflicts
                    catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                        bat "docker stop interview-regulator-web"
                        bat "docker rm interview-regulator-web"
                    }
                    
                    // Run the newly built container on port 3000
                    bat "docker run -p 3000:80 -d --name interview-regulator-web ${IMAGE_NAME}:latest"
                }
            }
        }
    }
}
