pipeline {
    agent { label 'workstation' }

    options {
        ansiColor('xterm')
    }
    stages {
        stage('Code Quality') {
            steps {
                sh 'sonar-scanner -Dsonar.host.url=http://172.31.34.243:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
            }
        }

        stage('Release') {
            steps {
                sh 'ip -4 addr show'
//                 sh 'env'
                echo 'CI' /////
            }
        }
    }
}
