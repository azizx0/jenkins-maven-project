pipeline {
    agent any

    tools {
        maven 'M2_HOME'  // Changed from 'M2_HOME' - use the tool name configured in Jenkins
        jdk 'JAVA_HOME' // Changed from 'JAVA_HOME' - use the JDK tool name configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', // Added branch specification
                    url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package' // Changed from 'bat' to 'sh' for Linux
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
                // OR if it's a multi-module project:
                // archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success { 
            echo 'Build réussi !' 
        }
        failure { 
            echo 'Build échoué !' 
        }
    }
}