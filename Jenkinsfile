pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compilation') {
            steps {
                echo 'Compilation du projet...'
                sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 compileJava'
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests et génération du rapport JaCoCo...'
                sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 test jacocoTestReport'
            }
        }

        stage('Sonar') {
            steps {
                echo 'Sonar'
            }
        }

        stage('JAR') {
            steps {
                echo 'Construction du JAR...'
                sh './gradlew jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé.'
        }
    }
}
