pipeline {
    agent any

    stages {
         stage('Git checkout') {

            steps{
                git 'https://github.com/utsab818/DevopsProject.git'
            }
         }

         stage('Unit Testing') {
            steps {
                sh 'mvn test'
            }
         }
    }
}