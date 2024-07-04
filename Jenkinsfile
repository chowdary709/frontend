pipeline {
    agent { label 'workstation' }

    options {
        ansiColor('xterm')
    }

    stages {
        stage(build){
            steps {
                sh """
                cd /root/frontend
                ls -la
                """
        }
        stage('Code Quality') {
            when {
                allOf {
                    branch 'main'
                    expression { env.TAG_NAME != env.BRANCH_NAME }
                }
            }
            steps {
                //sh 'sonar-scanner -Dsonar.host.url=https://sonar.chaitu.net -Dsonar.login=admin -Dsonar.password=@123Chaitu -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
                echo "hello"
            }
        }
        stage('Release') {
            when {
                expression { env.TAG_NAME ==~ ".*" } // any tag name it should be run
            }
            steps {
                sh 'env'   // Print the environment variables
                echo 'CI'
            }
        }
    }
}
