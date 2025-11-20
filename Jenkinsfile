pipeline {
    agent any

    tools {
        maven 'M2_HOME'  // Using your actual Maven tool name
        jdk 'JAVA_HOME'  // Using your actual JDK tool name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                dir('student-management') {  // Navigate to the subdirectory with POM.xml
                    sh 'mvn clean package'
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'student-management/target/*.jar', allowEmptyArchive: true
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