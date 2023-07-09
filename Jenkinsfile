pipeline{
  agent any

  stages {
    stage ('SCA SCAN'){
      steps {
        sh 'curl -sSL "https://download.sourceclear.com/ci.sh" | sh'
      }
    }

    stage ('ZIP do Projeto') {
      steps {
        sh 'zip -r projeto.zip .'
      }
    }
  }
}
