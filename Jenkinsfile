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

    stage ('Veracode Upload and Scan') {
      steps {
        sh 'curl https://repo1.maven.org/maven2/com/veracode/vosp/api/wrappers/vosp-api-wrappers-java/23.4.11.2/vosp-api-wrappers-java-23.4.11.2.jar -o veracode-wrapper.jar'
        sh 'java -jar veracode-wrapper.jar -vid ${APIID} -vkey ${APIKEY} -action UploadAndScan -appname "NodeGoat - Jenkins" -createprofile true -autoscan true -filepath projeto.zip -version ${BUILD_NUMBER}'
      }
    }

    stage ('Veracode Pipeline Scan') {
      steps {
        sh 'curl -O https://downloads.veracode.com/securityscan/pipeline-scan-LATEST.zip'
        sh 'unzip pipeline-scan-LATEST.zip pipeline-scan.jar'
        sh 'java -jar pipeline-scan.jar
                  --veracode_api_id "${APIID}"
                  --veracode_api_key "${APIKEY}"
                  --file "projeto.zip"'
      }
    }
  }
}
