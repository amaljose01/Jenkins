pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/amaljose01/Jenkins.git'
            }
        }
        stage('Install Python and Dependencies') {
            agent {
                docker {
                    image 'jenkins/jenkins:lts'
                    args '-v /var/run/docker.sock:/var/run/docker.sock'
                }
            }
            steps {
                // Install Python in the Jenkins container
                sh '''
                    apt-get update
                    apt-get install -y python3 python3-pip
                '''
                // Install Python dependencies
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'python3 script.py'  // Using python3 since that's what will be installed
            }
        }
    }
}
