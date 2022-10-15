pipeline {
    
    agent any
    
    stages {
        
        stage ('Create Helm Package') {
            steps {
                sh "pwd"
                dir('my-helm-charts'){
                    sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                    sh "helm package Charts/simplewebapp"
                }

            }
        }
        
        stage ('K8S delete deployment') {
            steps {
                sh "pwd"
                sh "helm list -a"
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
