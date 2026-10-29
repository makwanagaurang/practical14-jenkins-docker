pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t practical14-site:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker rm -f practical14-site || true'
                sh 'docker run -d --restart unless-stopped --name practical14-site -p 80:80 practical14-site:latest'
            }
        }
    }
}
