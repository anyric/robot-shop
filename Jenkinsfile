node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kubectl apply -f ./k8s/cart-deployment.yaml")
        sh("kubectl apply -f ./k8s/cart-service.yaml")
      }
    }
  }
  catch (err) {
    throw err
  }
}