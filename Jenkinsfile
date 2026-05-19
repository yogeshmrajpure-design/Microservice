pipeline {
    agent any

    stages {

        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                    kubectl config current-context
                    kubectl get nodes
                    kubectl apply -f deployment-service.yml
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get ns
                    kubectl get pods -n webapps
                    kubectl get svc -n webapps
                '''
            }
        }
    }
}
