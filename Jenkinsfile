pipeline {
    agent any

    environment {
        SONAR_HOST_URL = 'http://localhost:9000/projects/create'
        SONAR_LOGIN = credentials('sonar-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compilation') {
            steps {
                echo 'Compilation du projet...'
                sh './gradlew compileJava'
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests et génération du rapport JaCoCo...'
                sh './gradlew test jacocoTestReport'
            }
        }

        stage('SonarQube') {
            steps {
                echo 'Analyse SonarQube...'
                withSonarQubeEnv('SonarQube') {
                    sh './gradlew sonarqube \
                        -Dsonar.projectKey=ton-projet \
                        -Dsonar.host.url=${SONAR_HOST_URL} \
                        -Dsonar.login=${SONAR_LOGIN}'
                }
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
