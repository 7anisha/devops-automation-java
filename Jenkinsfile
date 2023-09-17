pipeline {
    agent any
    tools{
        
        maven 'maven'
    }
   
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/7anisha/devops-automation-java.git']]])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                   bat 'docker build -t anishaaaaa/devops-integration .'
                }
            }
        }
       stage('Push image to Hub'){
            steps{
                script{
                   bat 'docker login -u anishaaaaa -p anisha12345'
                   bat 'docker push anishaaaaa/devops-integration'
                }
            }
        
		}
    }



}
