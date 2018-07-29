#!groovy
pipeline {
    agent any
    stages {
        stage('GET_SOURCE'){
            steps{
                checkout scm                
            }
        }
        stage('BUILD') {
            steps {
                echo "Hello world"
                sh '/usr/bin/docker ps'
            }
        }
    }
}
