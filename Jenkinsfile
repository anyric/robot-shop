node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Deploy'){
      if(env.BRANCH_NAME == 'master') {
        sh("kompose --file docker-compose.yaml up")
      }
    }
  }
  catch (err) {
    throw err
  }
}