pipeline {
    agent any

    stages {

        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    credentialsId: 'k8-token',
                    namespace: 'webapps'
                ]]) {

                    sh '''
                        kubectl get nodes
                        kubectl apply -f deployment-service.yml
                    '''
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    credentialsId: 'k8-token',
                    namespace: 'webapps'
                ]]) {

                    sh '''
                        kubectl get pods -n webapps
                        kubectl get svc -n webapps
                    '''
                }
            }
        }
    }
}
