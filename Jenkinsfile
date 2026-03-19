pipeline {
    agent any
    tools {
        maven "Maven"
    }
    stages {
        stage("Build Maven") {
            steps {
                checkout scm
                
                bat 'mvn clean install'
            }
        }
        
        stage("Build Docker Image") {
            steps {
                script {
                    bat 'docker build -f src/Dockerfile -t patkneves/comp367-lab2 .'
                }
            }
        }
        
        stage("Push Docker Image") {
            steps {
                script {
                    withCredentials([string(credentialsId: 'Credential_DockerHubPass', variable: 'DOCKERHUB_PASS')]) {
                        bat 'docker login -u patkneves -p %DOCKERHUB_PASS%'
                        
                        bat 'docker push patkneves/comp367-lab2'
                    }
                }
            }
        }
    }
}