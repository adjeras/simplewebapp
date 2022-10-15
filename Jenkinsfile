pipeline {
    
    agent any
    
    stages {
        
        stage ('Terraform init') {
            steps {
                sh "pwd"
                //dir('terraform'){
                //    sh "pwd"
                //    sh label: '', script: 'terraform init'
                }
                sh "pwd"
            }
        }
        
        stage ('K8S delete deployment') {
            steps {
                //withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: '', credentialsId: 'K8Snew', namespace: '', serverUrl: '']]) {
                //    sh "kubectl delete deployment mobileyeapp"
                }
            }
        }        

        stage ('K8S Deploy') {
            steps {
                //withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: '', credentialsId: 'K8Snew', namespace: '', serverUrl: '']]) {
                //    sh "kubectl apply -f manifests/deployment.yml"
                }
            }
        }        
    }
}
