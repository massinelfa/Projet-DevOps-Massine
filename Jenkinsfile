pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                dir('devops-app') {
                    sh 'mvn clean test package'
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'devops-app/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                echo 'Déploiement simulé : application prête'
            }
        }
    }
}
