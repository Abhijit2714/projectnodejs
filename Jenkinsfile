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
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', url: 'https://index.docker.io/v1/', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh '''
                            echo "Username: $USERNAME"
                            echo "Password: $PASSWORD"
                            # Use the credentials in your commands
                        '''
                        sh 'docker login -u $USERNAME -p $PASSWORD'
                        sh 'docker tag helloproject abhijitdhamne/helloproject'
                        sh 'docker push abhijitdhamne/helloproject:latest'
                    }
                }
            }
        }
        stage('Apply Kubernetes files') {
            steps {
                script {
                    withKubeConfig([credentialsId: '4fe870b1-28e3-471b-b6e4-c5a3a1f7371c', serverUrl: 'https://192.168.1.34:6443']) {
                      sh 'kubectl apply -f deployment.yaml'
                    }
                }
            }    
        }
    }
}

