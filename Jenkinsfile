node {
  try {
    stage('Checkout') {
      checkout scm
    }
    // stage('Deploy'){
    //   if(env.BRANCH_NAME == 'master') {
    //     sh(" echo kubectl get pods --all-namespaces")
    //     sh("kubectl apply -f ./k8s/cart-deployment.yaml")
    //     sh("kubectl apply -f ./k8s/cart-service.yaml")
    //   }
    // }

    stage('Deploy') {
      withKubeConfig([serverUrl: 'https://104.155.31.202']) {
        sh 'kubectl apply -f K8s/descriptors/ --namespace=robot-shop'
      }
    }
  }
  catch (err) {
    throw err
  }
}