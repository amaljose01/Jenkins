pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://your-git-repository-url.git'
            }
        }
        stage('Install Dependencies') {
            agent {
                docker {
                    image 'python:3.9'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'python your_script.py'
            }
        }
    }
}
