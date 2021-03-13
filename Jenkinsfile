pipeline {
  agent any
  environment {
    RELEASE='20.04' 
  }
  stages {
    stage('Build') {
      agent any
      environment{
        LOG_LEVEL='INFO'
      }
      steps {
        echo "Building relase $RELEASE with log level $LOG_LEVEL..."
      }
    }
    
    stage('Test') {
      steps{
        echo "Testing relase $RELEASE..." 
      }
    }
    
      stage('Deploy') {
        input{
          message 'Deploy?'
          ok 'Do it!'
          parameters {
            string(name: 'TARGET_ENVIRONMENT', defaultValue: 'PROD', description: 'Target deployment environment') 
          }
        }
        
        steps {
          echo "Deploying relase $RELEASE to environment $TARGET_ENVIRONMENT" 
        }
    }
  }
  
  post{
    always {
      echo 'Prints whether deploy happened or not, succuss or failure' 
    }
  }
}
