node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Install docker') {
      sh 'sudo apt-get install apt-transport-https -y'
      sh 'sudo apt-get install -y docker.io'
      sh 'sudo systemctl start docker'
      sh 'sudo systemctl enable docker'
    }
    stage('Build Docker test'){
     sh 'docker-compose build'
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master'){
        sh("kubectl --namespace=production apply -f k8s/descriptors/")
      }
    }
  }
  catch (err) {
    throw err
  }
}