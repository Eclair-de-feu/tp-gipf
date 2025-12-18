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
                sh './gradlew -Dhttp.proxyHost=proxy1-rech -Dhttp.proxyPort=3128 compileJava'
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests et génération du rapport JaCoCo...'
                sh './gradlew test jacocoTestReport'
            }
        }

        stage('JAR') {
            steps {
                echo 'Construction du JAR...'
                sh './gradlew Jar'
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé.'
        }
    }
}
