pipeline {
    agent {
        docker {
            image 'node:lts-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('NPM Install') { 
            steps {
                sh 'npm install' 
            }
        }
		stage('NPM Build'){
			steps {
				sh 'npm run build'
			}
		}
		stage('Deploy NGINX Container'){
			steps{
				sh 'echo Deployed.'
			}
		}
    }
}