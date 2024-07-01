pipeline {
    agent { label 'workstation' } // Define the agent where the pipeline will run

    stages {
        stage('Code Quality') {   // This stage runs only on the 'main' branch, and only if TAG_NAME is different from BRANCH_NAME
            when {
                allOf {
                    branch 'main'  // Check if the branch being built is 'main'
                    expression { env.TAG_NAME != env.BRANCH_NAME } // TAG_NAME మరియు BRANCH_NAME విలువలు అసమానమైనప్పుడే రన్ అవుతుంది.
                }
            }
            steps {  // Run the SonarQube scanner for code quality analysis
                sh 'sonar-scanner -Dsonar.host.url=http://172.31.34.243:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
            }
        }

        stage('Release') {  // This stage runs only when TAG_NAME is set (not empty)
            when {
                expression { env.TAG_NAME ==~ ".*" }
            }
            steps {
                sh 'env'
                echo 'CI' //
            }
        }
    }
}
