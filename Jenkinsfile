pipeline {
    agent any

    tools {
        maven 'Maven-3.9.12'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/Leogabriele/java-tomcat-maven-example.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat '''
                copy target\\*.war C:\\apache-tomcat-9.0\\webapps\\
                '''
            }
        }
    }

    post {
        failure {
            echo 'Build or deploy failed!'
        }
        success {
            echo 'Build and deployment successful!'
        }
    }
}
