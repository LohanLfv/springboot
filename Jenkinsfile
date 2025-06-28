pipeline {
    agent any
    tools {
       maven 'localMaven'
       jdk "Java17"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout your source code from version control
                    git branch: 'master', credentialsId: 'jenkins', url: 'https://github.com/LohanLfv/springboot.git';
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the Maven project
                    sh "mvn clean package"
                }
            }
        }
    stage('Deploy to Nexus') {
            steps {
                script {
                    // Deploy the WAR file to Nexus Repository
                    nexusArtifactUploader(
                        nexusVersion: 'nexus3',
                        protocol: 'http',
                        serverId: '192.168.244.147:8081',
                        groupId: 'efrei',
                        version: '0.0.1',
                        repository: 'AppSpring',
                        credentialsId: 'nexusCredential',
                        nexusUrl: '192.168.244.147:8081',
                        artifacts: [
                            [artifactId: 'efrei-0.0.1-SNAPSHOT',
                             classifier: '',
                             file: 'target/efrei-0.0.1-SNAPSHOT.jar',
                             type: 'jar']
                        ]
                    )
                }
            }
        }

    }

}



