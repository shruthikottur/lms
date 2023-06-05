@Library("shruthi-libs") _
pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', credentialsId: 'shruthikottur', url: 'https://github.com/shruthikottur/lms.git'
            }
        }      
        stage('maven build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Dev deploy'){
            steps{
                tomcatDeploy("ec2-user","172.31.10.100","tomcat-dev","lms")
            }
        }
    }
}
