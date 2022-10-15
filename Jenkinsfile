pipeline {
    
    agent any
    
    stages {
        
        stage ('Create Helm Package') {
            steps {
                sh "pwd"
                sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                dir('my-helm-charts'){
                    sh "sed -i 's/version:.*/version: 0.1.${env.BUILD_ID}/g' Charts/simplewebapp/Chart.yaml"
                    sh "helm package Charts/simplewebapp"
                    sh "mv simplewebapp-0*.tgz Packages/"
                    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                    echo "Running ${env.BUILD_NUMBER} on ${env.JENKINS_URL}"
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
