pipeline {
  agent {
    node {
      label 'master'
    }
    
  }
  stages {
    stage('error') {
      steps {
        parallel(
          "Build": {
            node(label: 'ST_DEBIAN') {
              build 'stashtest1'
            }
            
            
          },
          "Build2": {
            node(label: 'ST_CENTOS') {
              build 'stashtest2'
              stash(name: 'stash2', allowEmpty: true, includes: 'foo.txt')
            }
            
            
          }
        )
      }
    }
    stage('Build3') {
      steps {
        node(label: 'ST_DEBIAN') {
          unstash 'stash2'
          build 'stashtest3'
        }
        
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