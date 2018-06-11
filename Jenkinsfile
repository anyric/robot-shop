node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Build Docker robot-sho'){
      sh("  /usr/local/bin/docker-compose build")
     
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kubectl --namespace=robot-shop apply -f ./K8s/descriptors/")
      }
    }
  }
  catch (err) {
    throw err
  }
}