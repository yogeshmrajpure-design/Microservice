pipeline {
    agent any

    stages {
    stage('Check Docker') {
        steps {
            sh 'which docker'
            sh 'docker version'
        }
    }
}
    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred',toolName: 'docker') {
                        sh "docker build -t adijaiswal/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push adijaiswal/adservice:latest "
                    }
                }
            }
        }
    }
}
