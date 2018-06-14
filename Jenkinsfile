node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh 'kubectl create -f K8s/descriptors/'
      }
    }
    stage('Post Deploy') {
      sh 'kubectl get pods --all-namespaces'
    }
  }
  catch (err) {
    throw err
  }
}