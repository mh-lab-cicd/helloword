pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Jenkins récupère ton code automatiquement ici
                echo 'Récupération du code...'
            }
        }
        stage('Build') {
            steps {
                echo 'Compilation en cours...'
                // Remplace par ta commande (ex: sh 'mvn install' ou sh 'npm install')
                // Sur Windows avec Jenkins, on utilise souvent 'bat' au lieu de 'sh'
                bat 'echo Hello World Build!' 
            }
        }
        stage('Test') {
            steps {
                echo 'Lancement des tests...'
                // Ta commande de test ici
            }
        }
    }
}
