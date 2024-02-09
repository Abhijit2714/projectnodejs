pipeline {
    agent {
        label 'infivitlinux222714'
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
                    sh 'echo 123456 | sudo -S docker build -t helloproject:latest .'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', url: 'https://index.docker.io/v1/')]) {
                        sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                        sh 'docker tag helloproject abhijitdhamne/helloproject'
                        sh 'docker push abhijitdhamne/helloproject:latest'
                    }
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    kubernetesDeploy(
                        kubeconfigId: '4fe870b1-28e3-471b-b6e4-c5a3a1f7371c',
                        configs: 'deployment.yaml',
                        enableConfigSubstitution: true
                    )
                }
            }
        }
    }
}

