pipeline {
  agent any
  
  parameters {
    //string(name: 'VERSION', defaultValue: '', description: 'Version to deploy to staging server')
    choice(name: 'VERSION', choices: ['1.1', '1.2', '1.3'], description: 'list of versions')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }
  tool {
    maven 'Maven'
  }
  
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
        echo "use shell script like mvn install"
      }
    }
    
     stage("Test") {
       when {
         expression {
           BRANCH_NAME == 'master' || BRANCH_NAME == 'umer-dev'
         }
       }
       when {
         expression {
           executeTests == true
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
        echo "Deploy version as: ${params.VERSION}"
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
