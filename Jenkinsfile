pipeline {
    agent any
    stages {
        stage('Git checkout') {
            steps {
                echo 'We are now checking out the git repository'
                git 'https://github.com/rohith-marigowda/javaProject.git' 
            }
        }
        stage('Build project') {
            steps {
                echo 'Build the above code using maven'
                sh 'mvn clean install' 
            }
        }
        stage('Push artifactory') {
            steps {
                echo 'Once the package is created using build tools, push the artifactory to nexus or jfrogg'
                echo 'Note: We are not pushing any of our artifacts into maven remote repository'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'deploy the artifactories into the environments'
                sh 'sudo cp /home/ec2-user/jenkins/workspace/cicd_master/target/*.war /opt/apache-tomcat-9.*/webapps/' 
            }
        }
    }
}
