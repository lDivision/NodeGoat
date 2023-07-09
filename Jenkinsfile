pipeline{
  agent any

  stages {
    stage ('SCA SCAN'){
      steps {
        curl -sSL https://download.sourceclear.com/ci.sh | sh
      }
    }
  }


  
}
