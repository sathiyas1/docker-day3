pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS = credentials('maven')  // Docker Hub Credentials ID
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/sathiyas1/guvi-day1.git'
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean"
                sh "mvn install"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t sathiyaseelan12/guvi-day1.git .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'maven') {
                        sh 'docker push sathiyaseelan12/guvi-day1.git'
                    }
                }
            }
        }
    }
}
