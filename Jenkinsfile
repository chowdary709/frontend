pipeline {
    agent { label 'workstation' }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Code Quality') {
//             when {
//                 allOf {
//                     branch 'main'  // Check if the branch being built is 'main'
//                     expression { env.TAG_NAME != env.BRANCH_NAME } // TAG_NAME మరియు BRANCH_NAME విలువలు అసమానమైనప్పుడే రన్ అవుతుంది.
//                 }
//             }
            steps {
                sh 'sonar-scanner -Dsonar.host.url=http://172.31.34.243:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=frontend -Dsonar.qualitygate.wait=true'
            }
        }

        stage('Release') {
//             when {
//                 expression { env.TAG_NAME ==~ ".*" }
//             }
            steps { /
                sh 'env'   // Print the environment variables
                echo 'CI'
            }
        }
    }
}
