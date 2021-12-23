pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('docker image pull') {
            steps {
                //sh
                bat "docker pull sharanyasb/selenium-docker"
            }
        }
        stage('Start Grid') {
            steps {
                //sh
                bat "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test') {
            steps {
                //sh
                bat "docker-compose up search-module book-flight-module"
            }
        }
    }
    post{

    	always{
    		archiveArtifacts artifacts: 'output/**'
    		bat "docker-compose down"
    	}	
    }

    
}
