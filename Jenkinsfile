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
        
        stage("test env vars") {
            steps {
                withEnv(["ACCESS_KEY_ID=$(env.AWS_ACCESS_KEY_ID)"]) {
                echo "ACCESS_KEY_ID is $(env.AWS_ACCESS_KEY_ID)"
                }
              
           }
        }
        
    }
}
