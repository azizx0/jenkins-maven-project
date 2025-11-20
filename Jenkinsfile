pipeline {
    agent { label 'windows' }

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
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                bat 'echo M2_HOME=%M2_HOME%'
                bat 'echo PATH=%PATH%'
            }
        }

        stage('Build') {
            steps {
                dir('student-management') {
                    bat 'call "%M2_HOME%\\bin\\mvn" clean package'
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
