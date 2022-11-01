pipeline {
    agent any

    stages {
         stage('Git checkout') {

            steps{
                git 'https://github.com/utsab818/DevopsProject.git'
            }
         }

         stage('UNIT Testing') {
            steps {
                bat 'mvn test'
            }
         }
         stage('Integration Testing') {
            steps {
                bat 'mvn verify -DskipUnitTests'
            }
         }
          stage('MAVEN Build') {
            steps {
                bat 'mvn clean install'
            }
         }
          stage('Static Code Analysis') {
            steps {
                bat 'mvn test'
            }
         }
          stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonarqube_api_key') {
                    bat 'mvn clean package sonar:sonar'
                }
            }
         }
         
    }
}