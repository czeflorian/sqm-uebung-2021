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
    stage('Build Docker test'){
     sh 'docker build -t generic-react-app --no-cache .'
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'main'){
        sh 'docker run -d -p 8081:80 generic-react-app'
      }
    }
  }
  catch (err) {
    throw err
  }
}