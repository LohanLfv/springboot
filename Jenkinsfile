pipeline {
    agent any
    tools {
        maven 'localMaven'    
        jdk 'Java17'          
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: 'main',
                        credentialsId: 'github-token',
                        url: 'https://github.com/LohanLfv/springboot.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh "mvn clean package"
                }
            }
        }

        stage('Deploy to Nexus') {
            steps {
                script {
                    nexusArtifactUploader(
                        nexusVersion: 'nexus3',
                        protocol: 'http',
                        nexusUrl: '192.168.244.147:8081',
                        groupId: 'efrei',
                        version: '0.0.1-SNAPSHOT',
                        repository: 'AppSpring',         
                        credentialsId: 'nexusCredential',
                        artifacts: [
                            [
                                artifactId: 'demo',        
                                classifier: '',
                                file: 'target/demo-0.0.1-SNAPSHOT.jar',
                                type: 'jar'
                            ]
                        ]
                    )
                }
            }
        }
    }
}
