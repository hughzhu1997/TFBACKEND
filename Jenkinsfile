pipeline {
    agent any
    
    environment {
        USER_NAME = "Hugh"
        USER_ID = 45
    }

    stages {
        stage('Build') {
            steps{ 
                 sh 'printenv'
                 sh 'docker build -t ecr-techchallengeapp .'
            }
        }
        
        stage("Using env vars") {
            environment {
                USER_PATH = "/home/hugh"
            }
            steps {
                echo "BUILD_NUMBER = ${env.BUILD_NUMBER}"
                sh 'echo BUILD_NUMBER = $BUILD_NUMBER'
                
                echo "Current user is ${env.USER_Name}"
                echo "Current user id is ${env.USER_ID} (type: ${env.USER_ID.class})"
                echo "Current user paht ${env.USER_PATH}"
           }
        }
        
    }
}
