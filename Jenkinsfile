pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        parallel(
          "TEST2": {
            sh 'echo "neco"'
            sleep 20
            
          },
          "TEST": {
            echo 'AHOj'
            
          },
          "FAIL": {
            error 'FAILED'
            
          }
        )
      }
    }
    stage('OK') {
      steps {
        parallel(
          "OK": {
            echo 'jojojo'
            
          },
          "job": {
            build 'name'
            
          }
        )
      }
    }
  }
}