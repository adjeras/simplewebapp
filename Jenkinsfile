pipeline {
    
    agent any
    
    stages {
        
        stage ('Terraform init') {
            steps {
                sh "pwd"
            }
        }
        
        stage ('K8S delete deployment') {
            steps {
                sh "pwd"
                dir('/home/azureuser/etoro/my-helm-charts/Charts/simplewebapp/'){
                    sh "pwd"
                }
            sh "pwd"
            }
        }

        stage ('K8S Deploy') {
            steps {
                sh "pwd"
                sh "helm list -a"
                }
        }
    }        
}
