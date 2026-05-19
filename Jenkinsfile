pipeline {
    agent any

    stages {

        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/lib/jenkins/.kube/config apply -f deployment-service.yml
                '''
            }
        }

        stage('verify Deployment') {
            steps {
                sh '''
                kubectl --kubeconfig=/var/lib/jenkins/.kube/config get svc -n webapps
                '''
            }
        }

    }
}
