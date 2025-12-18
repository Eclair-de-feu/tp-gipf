pipeline {
    agent any

    stages {
        stage('Compilation') {
            steps {
                echo 'Compilation'
                sh './gradlew -Dhttp.proxyHost=proxy1-rech -Dhttp.proxyPort=3128 compileJava'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Sonar') {
            steps {
                echo 'Sonar....'
            }
        }
        stage('JAR') {
            steps {
                echo 'JAR....'
            }
        }
    }
}
