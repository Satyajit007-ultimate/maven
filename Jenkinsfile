pipeline {
    agent any

    tools {
        maven 'Maven3' // The name of Maven tool configured in Jenkins
    }

    environment {
        NEXUS_CREDS = credentials('nexus-creds')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Satyajit007-ultimate/maven.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh """
                  mvn deploy -Dnexus.username=${NEXUS_CREDS_USR} \
                             -Dnexus.password=${NEXUS_CREDS_PSW}
                """
            }
        }
    }

    post {
        always { cleanWs() }
    }
}
