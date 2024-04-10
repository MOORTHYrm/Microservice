pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2016E5D78F93A4399A7F15B92C7CEEEE.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2016E5D78F93A4399A7F15B92C7CEEEE.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
