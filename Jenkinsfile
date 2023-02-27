pipeline{
  agent any
         
   stages{
  
      stage("Build"){
          steps{ 
               
            sh 'printenv'
            sh 'docker build -t ecr-techchallengeapp .'
              
    
                 }
            }
        
       
    
    
     stage("Push ECR"){
        steps{ 
        withEnv(["AWS_ACCESS_KEY_ID=$(env.AWS_ACCESS_KEY_ID)","AWS_SECRET_ACCESS_KEY=$(env.AWS_SECRET_ACCESS_KEY)","AWS_DEFAULT_REGION=$(env.AWS_DEFAULT_REGION)"])   { 
          sh 'docker login -u AWS -p $(aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/m4z9f5q8)' 
          sh  'docker build -t ecr-techchallengeapp .'
          sh 'docker tag ecr-techchallengeapp:latest  public.ecr.aws/m4z9f5q8/ecr-techchallengeapp""$BUILD_ID""'
          sh 'docker push public.ecr.aws/m4z9f5q8/ecr-techchallengeapp:latest:""$BUILD_ID"" '
          
          
          
            }
        }    
        
     }
     
 }
}
