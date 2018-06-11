node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kubectl get namespace robot-shop || kubectl create namespace sock-shop")
        sh("kubectl apply -n robot-shop -f docker-compose.yaml")
      }
    }
  }
  catch (err) {
    throw err
  }
}