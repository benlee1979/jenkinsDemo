pipeline {
  agent any
  environment {
    RELEASE='20.04' 
  }
  stages {
    stage('Build') {
      environment{
        LOG_LEVEL='INFO'
      }
      
      parallel{
        stage('linux') {
          steps {
            echo "Building relase $RELEASE with log level $LOG_LEVEL..."
          }
        }
        
       stage('WINDOW') {
          steps {
            echo "Building relase $RELEASE with log level $LOG_LEVEL..."
          }
        }
        
       stage('DOS') {
          steps {
            echo "Building relase $RELEASE with log level $LOG_LEVEL..."
          }
        }
      }
    
    }
    
    stage('Test') {
      steps{
        echo "Testing relase $RELEASE..." 
      }
    }
    
      stage('Deploy') {
        input{
          message 'Do you want to deploy?'
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
