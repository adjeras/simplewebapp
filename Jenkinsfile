pipeline {
    
    agent any
   
    parameters {
      choice choices: ['Upgrade', 'Install', 'Destroy'], description: 'Choose the installation type for this project', name: 'ChooseOption'
    } 

    stages {
        
        stage ('Create Helm Package') {
            steps {
                sh "pwd"
                sh "echo Choice: ${params.ChooseOption}"
                sh "mv templates values.yaml Chart.yaml my-helm-charts/Charts/simplewebapp/"
                dir('/var/lib/jenkins/workspace'){
                    sh "git clone git@github.com:adjeras/my-helm-charts.git"
                }
                dir('/var/lib/jenkins/workspace/helmDeploy/my-helm-charts'){
                    sh "sed -i 's/version:.*/version: 0.1.${env.BUILD_ID}/g' Charts/simplewebapp/Chart.yaml"
                    sh "helm package Charts/simplewebapp"
                    sh "mv simplewebapp-0*.tgz ~/workspace/my-helm-charts/Packages/"
                    sh "helm repo index ~/workspace/my-helm-charts/"
                }
            }
        }
        
        stage ('Push Helm chart to my-helm-charts repo') {
            steps {
                sh "pwd"
                dir('/var/lib/jenkins/workspace/my-helm-charts'){
                    sh "git add *"
                    sh 'git commit -m "Jenkins add helm"'
                    sh "git push origin main"
                }
                sleep 50
                sh "helm list -a"
            }
        }

        stage ('Installthe latest Helm chart on the AKS cluster') {
            steps {
                sh "helm repo update"
                sleep 5
                sh "helm search repo my-helm-charts -l --devel"
                sh "helm repo update"
                sleep 5
                if (params.ChooseOption == 'Upgrade') {
                    sh "helm upgrade simplewebapp my-helm-charts/simplewebapp"
                } elseif (params.ChooseOption == 'Install') {
                    sh "helm install simplewebapp my-helm-charts/simplewebapp"
                } else {
                    sh "helm delete my-helm-charts/simplewebapp"
                }
           }
        }

        stage ('Clean workspace dir') {
            steps {
                dir('/var/lib/jenkins/workspace'){
                    sh "rm -rf *"
                }
                sh "helm list -a"
            }
        }
    }
}        
