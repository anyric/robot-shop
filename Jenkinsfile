node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kompose up -f ./docker-compose.yaml")
      }
    }
  }
  catch (err) {
    throw err
  }
}