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
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqube_api_key') {
                        bat 'mvn clean package sonar:sonar'
                }
                }
            }
         }

         stage('Quality Gate Check') {
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonarqube_api_key'
                }
            }
         }
    }
}