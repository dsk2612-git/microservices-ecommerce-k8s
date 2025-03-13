pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DA5BD784BD534FC882E6268AFC57DF88.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f kuberenetes-manfest-file.yaml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DA5BD784BD534FC882E6268AFC57DF88.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc"
                }
            }
        }
    }
}
