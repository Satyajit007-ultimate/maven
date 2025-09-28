pipeline {
    agent any

    tools {
        maven 'Maven3' // Must match the Maven tool configured in Jenkins
    }

    environment {
        NEXUS_CREDS = credentials('9049cbee-fba2-41fd-872d-8a9c1a654ebc') // Jenkins credentials ID for Nexus
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
