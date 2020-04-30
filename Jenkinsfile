pipeline {
  agent any
  stages {
    stage('Clean Workspace'){
      steps {
          script {
          // Clean Up
          sh 'echo "cleaning Up workspace"'
        }
        cleanWs()

      }
    }
    
    stage('Build') {
      steps {
        script {
          // Build
          sh 'echo "Building Stage"'
          sh 'echo "Current Directory" ls -latr'
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