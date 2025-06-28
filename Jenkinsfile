pipeline {
    agent any
    tools {
       maven 'localMaven'
       jdk "Java8"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout your source code from version control
                    git branch: 'master', credentialsId: 'jenkins', url: 'https://gitlab.com/groupepoc/efrei.git';
                }
            }
        }
    }
}
