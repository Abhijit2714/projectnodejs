pipeline {
    agent {
        label 'infivitlinux222714'
    }
    environment {
        DOCKER_CREDENTIALS = credentials('2dbea0a2-9f04-4e85-8aa2-6061be55b590') // Replace 'docker-hub-credentials-id' with the ID of your Docker Hub credentials
    }
    stages { 
        stage('Build') {
            steps {
                sh 'echo "Hello, world!"'
                // Add more shell commands as needed
            }
        }
        stage('Check Docker Version') {
            steps {
                script {
                    // Run Docker version command and capture output
                    def dockerVersion = sh(script: 'docker --version', returnStdout: true).trim()

                    // Print Docker version
                    echo "Docker Version: ${dockerVersion}"
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'echo 123456 |sudo -S docker build -t helloproject:latest .'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS) {
                        docker.image('helloproject').push('latest')
                    }
                }
            }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
}
