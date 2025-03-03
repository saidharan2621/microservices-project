pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3E1D43D387E3D040FFFD4467FC494189.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'myeks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3E1D43D387E3D040FFFD4467FC494189.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
