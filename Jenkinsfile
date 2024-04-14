pipeline {
    agent any

    stages {
        stage('deploy to k8s cluster') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DD15483D80B8FBCB0AFD17289DBDD88F.gr7.ap-south-1.eks.amazonaws.com']]) {
             sh "kubectl apply -f deployment-service.yml"
             sleep 60
              }
            }
        }
        
        stage('verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://DD15483D80B8FBCB0AFD17289DBDD88F.gr7.ap-south-1.eks.amazonaws.com']]) {
               sh 'kubectl get all -n webapss'
              }
            }
        }
    }
}

