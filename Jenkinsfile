node {
  try {
    stage('Checkout') {
      checkout scm
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