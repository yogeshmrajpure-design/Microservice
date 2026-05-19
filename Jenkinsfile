pipeline {
    agent any

    stages {

        stage('Deploy To Kubernetes') {
            steps {

                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-1',
                    contextName: '',
                    credentialsId: 'k8-token_new_one',
                    namespace: 'webapps',
                    serverUrl: 'https://E52DA05CA5963A1B5F8895104CD686F8.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {

                    sh 'kubectl apply -f deployment-service.yml'

                }
            }
        }

        stage('Verify Deployment') {
            steps {

                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-1',
                    contextName: '',
                    credentialsId: 'k8-token_new_one',
                    namespace: 'webapps',
                    serverUrl: 'https://E52DA05CA5963A1B5F8895104CD686F8.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {

                    sh 'kubectl get svc -n webapps'

                }
            }
        }

    }
}
