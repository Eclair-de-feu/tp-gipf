pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout..'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh './gradlew build' 
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh './gradlew test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
                sh 'cp build/libs/mon-application.jar /path/to/deploy'
            }
        }
    }
}
