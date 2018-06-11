node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh 'kubectl apply -f K8s/descriptors/ --namespace=robot-shop'
      }
    }
  }
  catch (err) {
    throw err
  }
}