pipeline {
    agent {
        docker {
            image 'docker:latest'
            // args '-v /root/.m2:/root/.m2'
        }
    }
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
          sh 'pwd' 
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