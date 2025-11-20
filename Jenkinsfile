pipeline {
    agent any

    tools {
        maven 'M2_HOME'
        jdk 'JAVA_HOME'
    }

    stages {
        stage('Checkout GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/azizx0/jenkins-maven-project.git'
            }
        }

        stage('Build Livrable') {
            steps {
                dir('student-management') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
    }

    post {
        success { 
            echo 'Build réussi ! Livrable créé dans target/' 
        }
        failure { 
            echo 'Build échoué !' 
        }
    }
}