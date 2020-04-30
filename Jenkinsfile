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

    stage('Post Deployment') {
        steps{
          post {
          always {
              echo 'This will always run'
          }
          success {
              echo 'This will run only if successful'
          }
          failure {
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
    }
  }
}