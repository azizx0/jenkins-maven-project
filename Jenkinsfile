pipeline {
    agent any

    tools {
        maven 'M2_HOME'   // Utilise la variable d'environnement M2_HOME pour Maven
        jdk 'JAVA_HOME'    // Utilise la variable d'environnement JAVA_HOME pour le JDK
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                // Le pom.xml est dans student-management, donc on build depuis ce sous-dossier
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
