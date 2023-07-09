pipeline{
  agent any

  stages {
    stage ('SCA SCAN'){
      steps {
        sh 'curl -sSL "https://download.sourceclear.com/ci.sh" | sh'
      }
    }
  }

  
}
