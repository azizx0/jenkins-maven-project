pipeline {
    agent { label 'windows' }  // Met ici le label exact de ton agent Windows

    tools {
        maven 'M2_HOME'
        jdk 'JAVA_HOME'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                dir('student-management') {
                    bat 'mvn clean package'
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
