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
                    git branch: 'main', credentialsId: 'jenkins', url: 'https://github.com/LohanLfv/springboot.git';
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
    }

}

