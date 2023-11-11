pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Cloning Git Repo') {
            steps {
                script {
                    sh 'git clone https://github.com/gyanavardhana/hva-coursepage.git'
                }
            }
        }

        stage('Installing Dependencies') {
            steps {
                script {
                    sh 'sudo apt install -y apache2'
                }
            }
        }

        stage('Moving Files') {
            steps {
                script {
                    sh 'sudo cp -r hva-coursepage/* /var/www/html'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }   
}
