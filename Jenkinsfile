
pipeline {
    agent any
    tools {maven "maven"}
    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/sathiyas1/guvi-day1.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('build to images') {
            steps {
                script {
                    sh 'docker build -t sathiyaseelan12/webapp1 .'
                }
            }
        }
        stage('push to hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker_cred', toolName: 'docker', url: 'https://index.docker.io/v1/') {
                              sh 'docker push sathiyaseelan12/webapp1'
                    }
                }
            }
        }
        
    }
}
