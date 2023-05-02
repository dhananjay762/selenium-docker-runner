pipeline {
    // master executor should be set to 0
    agent any
    stages {
		stage('Pull Latest Image'){
            steps{
                bat "docker pull dhananjay762/selenium-docker"
            }
        }
		stage('Start Grid'){
            steps{
                bat "docker-compose up -d hub chrome firefox"
            }
        }
        stage('Run Test'){
            steps{
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