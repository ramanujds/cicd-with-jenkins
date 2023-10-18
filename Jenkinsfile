// defiine stages
pipeline {
    agent any
    tools{
        maven 'maven-3.9.5'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ramanujds/cicd-with-jenkins.git']]])
                sh 'mvn clean package'
                echo 'Build completed'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn test'
                echo 'Testing completed'
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building Docker Image...'
                sh 'docker build -t ram1uj/cicd-with-jenkins:latest .'
                echo 'Docker Image Build completed'
            }
        }
        
    }
}
