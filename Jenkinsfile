@Library("shruthi-libs") _
pipeline {
    agent any

    stages {
        stage('git checkout') {
            when {
                branch "develop"
            }
            steps {
                git branch: 'main', credentialsId: 'shruthikottur', url: 'https://github.com/shruthikottur/lms.git'
            }
        }      
        stage('maven build'){
            when {
                branch "develop"
            }
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Dev deploy'){
            when {
                branch "develop"
            }
            steps{
                tomcatDeploy("ec2-user","172.31.10.100","tomcat-dev","lms")
            }
        }
         stage('stage deploy'){
            when {
                branch "stage"
            }
            steps{
               echo "stage deploy here"
            }
        }
        stage('prod deploy'){
            when {
                branch "main"
            }
            steps{
                 echo "prod deploy here"
            }
        }
}
}
