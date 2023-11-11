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
        stage('Testing') {
            steps {
                script {
                    sh 'curl -I http://20.193.134.120/ > output.txt'
                sh "if grep -q 'HTTP/1.1 200 OK' output.txt; then echo 'The status code is 200 OK'; else echo 'The status code is not 200 OK'; fi"
                }
            }
        }

    }
    post {
        always {
            cleanWs()
        }
        success {
            script {
                sh 'sudo rm -r /var/www/html/*'
                sh 'sudo apt remove --purge -y apache2'
                sh 'echo bye bye task done'
            }
        }
    }   
}
