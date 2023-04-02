pipeline {
  agent any
  
  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS = credentials('umerfat')
  }
  
  stages {
    
    stage("Build") {
      
//       when {
//          expression {
//            BRANCH_NAME == 'master' || CODE_CHANGES == true
//          }
//        }
      
      steps {
        echo "Building application"
        echo "App version: ${NEW_VERSION}"
      }
    }
    
     stage("Test") {
       when {
         expression {
           BRANCH_NAME == 'master' || BRANCH_NAME == 'umer-dev'
         }
       }
      steps {
        echo "Testing application"
      }
    }
    
     stage("Deploy") {
      steps {
        echo "Deploying application"
        echo "Deploying with credentails ${SERVER_CREDENTIALS}"
        // we can use wrappers as well to fetch Jenkins Credentials
//         withCredentials([
//           usernamePassword(credentials: 'umerfat', userVariable:USER, passwordVaraible:PWD)
//         ]) {
//           echo "some script ${USER} ${PWD}"
//         }
      }
    }
    
  }
  
  post {
    
    always {
      echo "Executes always"
    }
    
    success {
      echo "Executes incase of build success"
    }
    
    failure {
      echo "Executes incase of build failure"
    }
  }
  
}
