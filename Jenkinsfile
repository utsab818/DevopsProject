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
                sh 'mvn test'
            }
         }
    }
}