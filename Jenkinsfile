pipeline {
    
    agent any
    
    stages {
        
        stage ('Terraform init') {
            steps {
                sh "pwd"
                dir('/home/azureuser/etoro/my-helm-charts/Charts/simplewebapp/'){
                    sh "pwd"
                }
            }
        }
        
        stage ('K8S delete deployment') {
            steps {
                sh "pwd"
                }
        }

        stage ('K8S Deploy') {
            steps {
                sh "helm list -a"
                }
        }
    }        
}
