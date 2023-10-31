pipeline{
   agent {
  label 'docker-slave'
}
    stages{
        stage('checkout'){
            steps{
                //checkout the code which has Dockerfile in it
                git branch: 'master', url: 'https://github.com/shreedevi1991/DockerAssignment.git'
            }
        }
        stage('Build Stage'){
            steps{
                //Build the docker image
                sh 'docker build -t my-image .'
                echo "image build done"
            }
        }
        stage('push Stage'){
            steps{
                // Authenticate Docker to your ECR registry
                sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/i7y4g8r2'
                sh 'docker tag my-image:latest public.ecr.aws/i7y4g8r2/dockerassignment-05:latest'
                sh 'docker push public.ecr.aws/i7y4g8r2/dockerassignment-05:latest'
            }
        }
        stage('Deploy stage'){
            steps{
                //push the image as a container to the docker server
                sh 'docker run -d --name assignment-005 my-image:latest'
            }
        }
    }
  }
