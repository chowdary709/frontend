pipeline {
    agent {
        label 'workstation'
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Code Quality') {
            steps {
                script {
                    sh 'sonar-scanner -Dsonar.host.url=https://sonar.chaitu.net -Dsonar.login=admin -Dsonar.password=@123Chaitu -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
                }
            }
        }
        stage('Release') {
            when {
                expression { env.TAG_NAME ==~ ".*" }
            }
            steps {
                script {
                    sh 'env'   // Print the environment variables
                    echo 'CI'
                }
            }
        }
    }
}

