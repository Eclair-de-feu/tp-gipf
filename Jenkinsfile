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

        stage('SonarQube Analysis') {
            steps {
                sh "./gradlew sonar \
                  -Dsonar.projectKey=tp-gipf \
                  -Dsonar.projectName='tp-gipf' \
                  -Dsonar.host.url=http://172.17.0.1:9000 \
                  -Dsonar.token=sqa_c40ee97f1eca2addebb6bae4eb9b03bab9777121"
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
