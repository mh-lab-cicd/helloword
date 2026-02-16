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
                script {
                    if (isUnix()) {
                        sh 'echo Hello World Build!'
                    } else {
                        bat 'echo Hello World Build!'
                    }
                }
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
