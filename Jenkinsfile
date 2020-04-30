pipeline {
  agent any
  stages {
    stage('Clean Workspace'){
      steps {
        cleanWs()
      }
    }


    stage('Checkout'){
            steps {
            checkout([$class: 'GitSCM', 
            branches: [[name: '*/feature/dockerise']], 
            doGenerateSubmoduleConfigurations: false, 
            extensions: [], 
            submoduleCfg: [], 
            userRemoteConfigs: [[url: 'https://gitlab.com/propitix/infrastructure/custom-development/tooling-website.git']]])

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