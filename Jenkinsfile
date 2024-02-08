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
                    sh 'docker build -t helloproject:latest .'
                }
            }
        }
        stage('Push Docker Image to ECR') {
            steps {
                script {
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAU5L46MC23JVF5HOS', credentialsId: 'eyJwYXlsb2FkIjoiTml0UW5pcTA2Q0x1YWlrVEowWjRGSS9oOG5rRG44T3g1L1luSzZQK0gyRC9MWDR2dkU2engzZ2JvVVdzOXhGcW5CWU9SQTlBZ2FjYnpUQXloSWN6RSttUmxReVFvSVRmWjBRWm9ZUHNJd0Vrbyt1TGpYTmUyZm1Ib3UzMldSV1J0RmM2L21CR3FHTGg4M0FCSkVWYnEzMHpJWVFYa3BlSnFpVFNJWFFCeXRhaGp1dnlWN0dBcThJL1YrRmlBTUZSVXAxdUZXZTBacWFDM1VZcTZPcEZMa3ZGbjhmVWZGT0hSZWdaSHZBcUZ0cGxOY3IyV2tBSXc5dlRnYnhrb3dkTnlPNW5RdGUyaTRDd3RJTkt6NVdDSkYrdVhHb2ovTHUxSWRPSVlibFd5YWlRWFdFaDRVd2FiT3gyVHhiUENBNkhMTFJGS29kM0cvQ05MenQya0lmT1VVWUhGaU5WeTh0NDZYVzNRQkNtRUc0V1BiR0hEMjhmbXo5ZmY4NHVYQVNDdXFlbmFqWnZTNGJ5cWpROVF2dndjU3Rad09DY0ZQZmVhZi9CYjJpb1FERjFCNDFxd2NLTVpZV0FVWTVGUWZsaGowWlU5OUhQeHdvc0ZrN1ZjWFhQMU0vamZpcDA0bU8wTVdMVi8vcURQeHBFZW93NGNiZkRzMzFwckIzUnU1OFdIYjh2bHFzSVc1YWJxM3ZvRHloTVFLdlVESnMyNWN5UTFFWDVUSkhKN2xBaTZSOEI0Yk02R0NvNGxRNVZGTXNYNmUyQjB5T1hkSjFPVmFlMkUycmRvZGw4cHFleEtGbW1odVVjVHR2cXJVYUloNDJwUmVJTGpRZERhK1ZZbWNPanBTUENmazdMejlTaGlveHcrTkg0cmNIZlZFdUF0a21xYmpNRXVWWm5FODNEYk9pQ2Y5Q29BVndpd0VNOU1YZ1hZNlVqZzNzZWxkNkRRckoyeW5oUldxUXVTK2Vta1ljLzVmQzdoMDdXdVhvYUtJTm5ONWtyaFNUSzJoMGpQcGc2T0lRMnFTVlo3b2x0R3M2K3hSTjlGMlBIL05OZTN2NmkyK3Y3MlNST1pyWURCR1VtM2Z3T1JDVnNVa04rM1ljNjVJM0ptTkl6RDhsZHg3akdHOHk1dTRGNGZqWERxK1J6cUlhZ0FWWXIwVWVmZFBJMmVLQkQvWitOa2p5eVljQ1UvVnUwNEhXVVRISGpOSENMT2pOclJVcnhGRTAxMmFPRDk0ZC8yY1NmbnV3TXlEbmI1Z3NWOVgyaDBtcmxLeXhuNTJGMFE0aUo0djltMHQ3aW5Ea3F3ZFBrZnVUTWY4cEhqc1dQWXJQU0xEOVNhaDRCU3lpaW55YlZnbjNQcENqSmU0a3N0MVg1M0xIR25sWXUvOEhVdTh1RTdjWGpldU5XREdseGVDTXFlM2pneHh2aGdjZTRsWGxEU3p6enlscWNUTWI2eFN5RmRDRlJSUTFSb0NoTTR2a0tjeEVZck5JRnZXcTlPY1luVDF4SGJnaWtNa1V4RUdKbXlTbnZzU3lNY3FFb0FQek9CdkJpRlFRM3k0ZGNoRDR3UEREWHFPN2JxSW1aMHMrS3JWSHhVOXAxZ1V2SDc5MWlJb0FjMmI2MGxEQmNBUGd5ZzM4Yi9BMGIzdE5NOG9MNFIvQk5vOC9FS0E9PSIsImRhdGFrZXkiOiJBUUVCQUhod20wWWFJU0plUnRKbTVuMUc2dXFlZWtYdW9YWFBlNVVGY2U5UnE4LzE0d0FBQUg0d2ZBWUpLb1pJaHZjTkFRY0dvRzh3YlFJQkFEQm9CZ2txaGtpRzl3MEJCd0V3SGdZSllJWklBV1VEQkFFdU1CRUVESHJhYkhFNWJTOWZ2YjNRZHdJQkVJQTdWaDFQK1NYZERRYVFxRGlldjJhb3loTnhuTGZzd0xEb2dGUGozTS81clFKYXJSMUhNa2dwcUhlMVZjZ2p3UW5ZNmRqck9sWUVkc0lFQXRBPSIsInZlcnNpb24iOiIyIiwidHlwZSI6IkRBVEFfS0VZIiwiZXhwaXJhdGlvbiI6MTcwNzM0MDMzM30=', secretKeyVariable: 'Twyhb6/etTgeq6S7bmQriAj1pndnl5k3vLO8Q3L0']]) {
                        docker.withRegistry('https://your-aws-ecr-uri', 'ecr') {
                            docker.image('your-aws-ecr-repo-uri:latest').push('latest')
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
