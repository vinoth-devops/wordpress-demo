#!groovy
pipeline {
    agent any
    stages {
        stage('GET_SOURCE'){
            steps{
                checkout scm
             }
        }
        
        stage('BUILD_IMAGE'){
            steps{
                echo 'Build docker image is starting'
                //It will build and push lastet version and specfic build version
                sh "docker build --label version=${env.BUILD_NUMBER} -t gcr.io/kubernetes-210413/wordpress -t gcr.io/kubernetes-210413/wordpress:${env.BUILD_NUMBER} ."
                sh "gcloud docker -- push gcr.io/kubernetes-210413/wordpress:${env.BUILD_NUMBER}" 
                sh "gcloud docker -- push gcr.io/kubernetes-210413/wordpress" 
                sh "docker rmi gcr.io/kubernetes-210413/wordpress:${env.BUILD_NUMBER}" 
            }
        }
        
        stage('DEPLOYMENT'){
            steps{
                sh "gcloud container clusters get-credentials devops-demo --zone us-east1-b --project kubernetes-210413"
                sh "helm install -n wordpress-${env.BUILD_NUMBER} ./helm/wordpress"
            }
        }
    }
}
