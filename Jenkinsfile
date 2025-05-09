pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'SonarQube'  // Nom de ton serveur SonarQube
        DOCKER_IMAGE_NAME = 'school-image' // Nom de l'image Docker
    }

    stages {
        stage('Cloner le code depuis GitHub') {
            steps {
                // Cloner ton repository GitHub
                git 'https://github.com/Imenetr26/school-projet.git'
            }
        }

        stage('Compiler le projet avec Maven') {
            steps {
                script {
                    // Compiler ton projet avec Maven
                    sh 'mvn clean install'
                }
            }
        }

        stage('Analyse SonarQube') {
            steps {
                script {
                    // Analyse le code avec SonarQube
                    sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$SONARQUBE_TOKEN'
                }
            }
        }

        stage('Construire l\'image Docker') {
            steps {
                script {
                    // Construire l'image Docker
                    sh 'docker build -t $DOCKER_IMAGE_NAME .'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline exécuté avec succès!'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}
