pipeline {
    agent any

    stages {
        stage('Deploy to k8') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0108B648FDF093F8DAF3DEED2B81DB26.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh 'kubectl apply -f deployment-service.yml'
                    sleep 60
                }
            }
        }
        
         stage('Verify Deployment') {
            steps {
                  withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0108B648FDF093F8DAF3DEED2B81DB26.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh 'kubectl get all -n webapps '
                    
                }
            }
        }
    }
}
