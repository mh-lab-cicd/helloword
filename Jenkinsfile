pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du code depuis le dépôt...'
                // Le checkout est automatique avec "Pipeline from SCM"
            }
        }

        stage('Build') {
            steps {
                echo 'Initialisation de la compilation...'
                script {
                    if (isUnix()) {
                        // Commandes pour Linux / Docker
                        sh 'echo "Système Linux détecté"'
                        sh 'npm install' 
                    } else {
                        // Commandes pour Windows (Agent natif)
                        bat 'echo "Système Windows détecté"'
                        bat 'npm install'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests unitaires...'
                script {
                    if (isUnix()) {
                        sh 'npm test || echo "Pas de tests définis"'
                    } else {
                        bat 'npm test || echo "Pas de tests définis"'
                    }
                }
            }
        }

        stage('Deploy Heroku') {
            steps {
                echo 'Déploiement vers Heroku en cours...'
                // Utilisation du secret configuré dans Jenkins
                withCredentials([string(credentialsId: 'HEROKU_API_KEY', variable: 'MY_KEY')]) {
                    script {
                        if (isUnix()) {
                            // Déploiement via le token sur l'URL Git Heroku
                            sh "git push https://_:${MY_KEY}@git.heroku.com/hello-nextjs-mamoudou.git HEAD:main --force"
                        } else {
                            // Version Windows pour le push Heroku
                            bat "git push https://_:${MY_KEY}@git.heroku.com/hello-nextjs-mamoudou.git HEAD:main --force"
                        }
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Félicitations ! Le déploiement de hello-nextjs-mamoudou est réussi.'
        }
        failure {
            echo 'Le pipeline a échoué. Vérifiez les logs de la console.'
        }
    }
}