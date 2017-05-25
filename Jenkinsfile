pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Bulding FW - OK'
        sleep 15
      }
    }
    stage('Build testware') {
      steps {
        parallel(
          "JOB1": {
            echo 'Bulding testware - OK'
            sleep 25
            
          },
          "JOB2": {
            build 'SandBox/TryToRun'
            
          }
        )
      }
    }
    stage('Test') {
      steps {
        parallel(
          "TEST1": {
            echo 'TEST1 OK'
            sleep 5
            
          },
          "TEST2": {
            echo 'TEST2 OK'
            sleep 20
            
          },
          "TEST300": {
            echo 'TEST3'
            sleep 5
            
          }
        )
      }
    }
    stage('Filip, procced to deploy?') {
      steps {
        parallel(
          "Filip, proceed to deploy?": {
            input 'Filip, proceed to deploy?'
            
          },
          "Roman, Proceed to deploy?": {
            input 'Roman, proceed to deploy?'
            git(url: 'testurl', branch: 'test', credentialsId: 'test', poll: true)
            
          }
        )
      }
    }
    stage('Deploy to production') {
      steps {
        parallel(
          "Deploy to production": {
            echo 'copy to folder'
            
          },
          "": {
            sh 'echo "Test of shell script"'
            
          }
        )
      }
    }
  }
  post {
    always {
      echo 'This will always run'
      
    }
    
    success {
      echo 'This will run only if successful'
      
    }
    
    failure {
      mail(to: 'rmalik@ra.rockwell.com', subject: "Failed Pipeline: ${currentBuild.fullDisplayName}", body: "Something is wrong with ${env.BUILD_URL}")
      echo 'This will run only if failed'
      
    }
    
    unstable {
      echo 'This will run only if the run was marked as unstable'
      
    }
    
    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
      
    }
    
  }
}