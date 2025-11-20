pipeline {
    agent any

    tools {
        maven 'Maven 3.6.3'
        jdk 'JDK17'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'student-management/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success { echo 'Build réussi !' }
        failure { echo 'Build échoué !' }
    }
}
