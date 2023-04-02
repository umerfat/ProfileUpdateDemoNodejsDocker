pipeline {
  agent any
  stages {
    
    stage("Build") {
      steps {
        echo "Building application"
        echo "App built"
      }
    }
    
     stage("Test") {
      steps {
        echo "Testing application"
      }
    }
    
     stage("Deploy") {
      steps {
        echo "Deploying application"
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
