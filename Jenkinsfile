pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/amaljose01/Jenkins.git'
            }
        }
        stage('Install Dependencies') {
            agent {
                docker {
                    image 'python:3.9'
                }
            }
            steps {
                // Make sure you're in the workspace where the cloned repo is
                dir("${env.WORKSPACE}") {
                    sh 'pip install -r requirements.txt'
                }
            }
        }
        stage('Run Tests') {
            steps {
                dir("${env.WORKSPACE}") {
                    sh 'python script.py'
                }
            }
        }
    }
}
