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
        stage('Deploy to Heroku') {
            steps {
                withCredentials([string(credentialsId: 'HEROKU_API_KEY', variable: 'HEROKU_API_KEY')]) {
                    // Installation du CLI Heroku si nécessaire ou utilisation de Git
                    script {
                        if (isUnix()) {
                            sh 'git push https://_:$HEROKU_API_KEY@git.heroku.com/hello-nextjs-mamoudou-f9b476d58f42.git HEAD:main --force'
                        } else {
                            bat 'git push https://_:%HEROKU_API_KEY%@git.heroku.com/hello-nextjs-mamoudou-f9b476d58f42.git HEAD:main --force'
                        }
                    }
                }
            }
        }
    }
}
