pipeline {
    agent any

    tools {
        maven 'Maven3'  // Nom du Maven configuré dans Jenkins
        jdk 'JDK11'     // Nom du JDK configuré dans Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du projet depuis GitHub...'
                git 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Construction du projet avec Maven...'
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                echo 'Archivage du livrable...'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo 'Build terminé avec succès !'
        }
        failure {
            echo 'Le build a échoué.'
        }
    }
}
