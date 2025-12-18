pipeline {
    agent any

    stages {
        stage('Build') {
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
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
