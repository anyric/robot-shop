node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Build Docker robot-shop'){
      sh 'sudo docker-compose build'
     
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kubectl --namespace=robot-shop apply -f ./K8s/descriptors/*")
      }
    }
  }
  catch (err) {
    throw err
  }
}