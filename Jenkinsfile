pipeline {
    agent any
    tools {
		maven 'Maven'
	}
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out...'
                checkout scm
            }
        }
        stage('Build') { 
            steps {
                echo 'Building...'
                bat 'mvn -B -DskipTests clean package' 
            }
        }
    }
}