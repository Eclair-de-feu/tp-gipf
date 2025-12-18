pipeline {
    agent any

    stages {
        stage('Compilation') {
            steps {
                echo 'Compilation'
                sh './gradlew compileJava'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew '
            }
        }
        stage('Sonar') {
            steps {
                echo 'Sonar....'
            }
        }
        stage('JAR') {
            steps {
                sh ''
            }
        }
    }
}
