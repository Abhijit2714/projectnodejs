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
                    sh 'echo 123456 |sudo -S docker build -t helloproject:latest .'
                }
            }
        }
        stage('Push Docker Image to ECR') {
            steps {
                script {
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAZRFP2HW4HBUVF5PI', credentialsId: 'eyJwYXlsb2FkIjoiWEttTTlvWlNZOFNDd1dKT0VRa1ZjRlhibmE3TUg5L3ZQQzZlSzJJVnZsQ3NkRFVtakhjVzhTdHhJOGxyQWlES3ZHMEdOa0p5YmNpd1F4akJYSzVzbXFJZm1kSCt3NnlUV0VNQVdoMGp3bnZ1NDJsYXcvMGdyT2xOS1dwTzFaNFhkZ0JMQzlpZU5HcUdEWXVLVzFMRldtbHpNZk9kbE92dnlYaEZvUytCVFVJOWlEOXNBVVRXU1lGTkMzUTM3d28yVHNXajBqdGF0R3prMEZoeDBVRHAzRm5qRWZUMzQrRkFvTzZrakVNeUNFSFdDOWJCL2dWL0hKVW43UFMzOTltNkVyL2YzNG1BL2lsYnV4MGREMlVtTGwyZmJUeEQ1NDEyV3k5eHJxU296bitnckNEMk95VjdDQmZHL0JYQkdsQUR4Rjl3b0toVk1VdlpCSkpVaVhKMmluQ0c0Zm9QZ2wvRFZzcDhad3VqcVRBaFp5cjY0ZmFRSHN5VmdUSDlmT3pXcmI0Nm9GUDc2QzNyV3JmTEJNRzYrSDdEYWdiYlpmR0NoRnpyVXJuc2hsUTlJa0tBYy9vTE9xSmc1bGVoS0dCNE1OTm9aNVptYW91WCtnamp6amp3cmdjcVNHbTFqSlRSQm1ldnVicnhBV3hlZUh4bXNxL0JNL29NM0FyMjBZNmQrTjR0bWYxbFYwRG5OVHhqUXliaVFRNEtZN3d0S29DbHFIWVp4UTJLaGVBUzZBQjNLdllzNDcwZkhDT0lCTkpyUWVvd1BjL0l0Wk9GMHZ5YlRTQXlZTGJCUHJzeENJZExKOTArS2ZEYzZaN0VFN2hJTWlIR2VFVDBtbmQrSUlHRC9xclNBVmhRZGpsYTBkTWdBZW5kVkZmc1RGR2liVlAxd1FIZDM5Uy9SV2ZUenlHalFXTnNta2tiNnowMmlPbnMrQzc2Q21nRmM4aEpCbUtmZXRRWFV3aEc1cFVmdmVoRHR0SnNNT2ltVnd2bm42bkxZRFUrTTFhemwrOXpQL0JaNVpLb21SdWFBR2RHTG5NSUt0QzJ0NGJFSXo5Q1dSTFBYOEtrT1BJOVhIMWpJNWpmV09McG9TS2w2TlJMcFJpR2Q0a1ZYWkZRZTJBQ09YSGpOd0s4Y2hBdHlsQ21IUzFXNXBwQWVzRjk2dE5xOEF6dG1rMlpHOG0wUHpMZnZudWJUbHVxM29BSWNiMUQzT0ljR0dxdUVBVm5Jd213Sy8waFNXZmhKOXBCTFpCZHF4TDRZTHhCckpXVmdzTzBTanFwcjJxa3dDMVRyS0o5TEQvV0VqM1NjN1ArZVpJNlpQR09vRXZQMzNzSHNMUWZCUWxkT0RaL0ZSbDFwWUtPMzUvbEo4S0ZiZ0pRZ1BYZTAvL01jaG85OXdPK0xBMm5uRk92TnVmQ3NySHFreFBsVExxdnUwTVN1dlBielY1YmhxODFFZVRNRStxeCtvQ29BMFN5cS9xQ2FDczk5SmlIWVlVZndmekVONlJTQ0EzN011ZkUvWVZGRzQ5aG8xbWlPMktMV2kwOEFaZGZSOGhGOGxZWFVFZGZNSVFjNERXQ1dhNHJpaFA5cHBLWG93RVVhUksxdHllY3pXK3pTcE9nMWFVaDRoZXRaRXpCVFFEZC8wQmEzWEdLdEo0bXJHdUYvbW55a1E9PSIsImRhdGFrZXkiOiJBUUVCQUhod20wWWFJU0plUnRKbTVuMUc2dXFlZWtYdW9YWFBlNVVGY2U5UnE4LzE0d0FBQUg0d2ZBWUpLb1pJaHZjTkFRY0dvRzh3YlFJQkFEQm9CZ2txaGtpRzl3MEJCd0V3SGdZSllJWklBV1VEQkFFdU1CRUVER3FINUN1U09ldnJ2M0dOemdJQkVJQTdCakNxZGpQb3VOQ1RNQ0huWUtuT3Vvd0doYmNINEZaK1ZLSlBCNVVJaFY0MnNpamFFWThtNVRhTndkTE9ZaHErRmxxc2R0VzdralJJVExrPSIsInZlcnNpb24iOiIyIiwidHlwZSI6IkRBVEFfS0VZIiwiZXhwaXJhdGlvbiI6MTcwNzUwMTk5Mn0=', secretKeyVariable: 'sbdqQ7EODqDzZMJro0KgGib3JfEECoxK0wLMuraT']]) {
                        docker.withRegistry('https://public.ecr.aws/n5t3z5z4', 'ecr') {
                            docker.image('public.ecr.aws/n5t3z5z4/projectnodejs:latest').push('latest')
                        }
                    }
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
