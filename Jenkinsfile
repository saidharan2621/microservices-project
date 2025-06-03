pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://192709CCEC259B9C6092FEA19EFD0781.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://192709CCEC259B9C6092FEA19EFD0781.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
