pipeline {
    agent any 

    stages {
        stage('Push to ECR') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'ecr:us-east-1:web_pp', url: 'https://655040006853.dkr.ecr.us-east-1.amazonaws.com/') {
                        echo "======== I am a DevOps Engineer ========"
                        sh "docker build -t web-app:1.2.2 ."
                        sh "docker tag web-app:1.2.2 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                        sh "docker push 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:latest"
                        sh "docker push 655040006853.dkr.ecr.us-east-1.amazonaws.com/web-app:1.2.2"
                    }
                }
            }
        }
        
        stage("Update ECS") {
            steps {
                sh "aws ecs update-service --cluster gift-app --service giftservice --force-new-deployment"
            }
        }
    }
}
