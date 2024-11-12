pipeline{
    agent any 
    
    stages{
        stage('push to ECR'){
          steps{
            script {
             withDockerRegistry(credentialsId: 'ecr:us-east-1:web_pp', url: '655040006853.dkr.ecr.us-east-1.amazonaws.com/'){
                  echo "========I am a DevOps Engineer ========"
                  sh "docker build -t web-app ."
                  sh "docker tag web-app:1.2.2 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                  sh "docker push 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                  sh "docker push 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:1.2.2"
             }  
            }  
          }
        }
      }
    
    }
