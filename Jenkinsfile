node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }
	stage('Check User and group'){
		echo "$USER"
	}
    stage('Build Docker'){
     sh 'docker build -t generic-react-app --no-cache .'
    }
    stage('Deploy'){
        sh 'docker run -d -p 8081:80 generic-react-app'
    }
  }
  catch (err) {
    throw err
  }
}