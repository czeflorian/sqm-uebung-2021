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
		stage('Build Docker Container'){
			steps{
				sh 'docker build . -t generic-react-app-nginx'
			}
		}
		stage('Deploy Docker Container'){
			steps{
				sh 'docker run -d -p 8081:80 generic-react-app-nginx'
			}
		}
    }
}