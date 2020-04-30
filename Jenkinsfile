pipeline {
  agent any
  stages {
    stage('Clean Workspace'){
      steps {
        cleanWs()
      }
    }
    
    stage('Build') {
      steps {
        script {
          // Build
          sh 'echo "Building Stage"'
        }
      }
    }


    stage('Test') {
      steps {
        script {
          // Build
          sh 'echo "Testing Stage"'
        }
      }
    }

    stage('Deploy') {
      steps {
        script {
          // Build
          sh 'echo "Deploy Stage"'
        }
      }
    }
  }
}