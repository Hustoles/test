pipeline {
  agent any
  stages {
    stage('') {
      steps {
        parallel(
          "TEST2": {
            sh 'echo "neco"'
            sleep 20
            
          },
          "TEST": {
            echo 'AHOj'
            
          }
        )
      }
    }
    stage('OK') {
      steps {
        echo 'jojojo'
      }
    }
  }
}