pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Debug Env') {
            steps {
                sh 'echo JAVA_HOME=$JAVA_HOME'
                sh 'echo M2_HOME=$M2_HOME'
                sh 'echo PATH=$PATH'
            }
        }

        stage('Build') {
            steps {
                dir('student-management') {
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
        success { echo 'Build réussi !' }
        failure { echo 'Build échoué !' }
    }
}
