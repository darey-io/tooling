pipeline {
  agent any

      environment 
    {
        PROJECT     = 'zooto-tooling-prod'
        ECRURL      = '059636857273.dkr.ecr.eu-central-1.amazonaws.com'
        ENVIRONMENT = 'dev'
    }

  stages {

    stage('Checkout')
    {
      steps {
      checkout([
        $class: 'GitSCM', 
        doGenerateSubmoduleConfigurations: false, 
        extensions: [],
        submoduleCfg: [], 
        // branches: [[name: '$branch']],
        userRemoteConfigs: [[url: "https://github.com/darey-io/tooling.git ",credentialsId:'GITHUB_CREDENTIALS']] 	
        ])
        
      }
        }

    // stage('Checkout Helm chart')
    // {
    //   steps {
    //   checkout([
    //     $class: 'GitSCM', 
    //     doGenerateSubmoduleConfigurations: false, 
    //     extensions: [[$class: 'RelativeTargetDirectory', 
    //         relativeTargetDir: 'helm']],
    //     submoduleCfg: [], 
    //     branches: [[name: 'master']],
    //     userRemoteConfigs: [[url: "https://gitlab.com/propitix/kubernetes/helm.git",credentialsId:'GIT_CREDENTIALS']]
    //     ])
        
    //   }
    //     }
          stage('Build preparations')
        {
            steps
            {
                script 
                {
                    // calculate GIT lastest commit short-hash
                    gitCommitHash = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
                    shortCommitHash = gitCommitHash.take(7)
                    // calculate a sample version tag
                    VERSION = shortCommitHash
                    // set the build display name
                    currentBuild.displayName = "#${BUILD_ID}-${VERSION}"
                    IMAGE = "$PROJECT-$ENVIRONMENT:$VERSION"
                }
            }
        }

    stage('Docker build') {
        steps {
            echo 'Build Dockerfile....'
            script {
                sh("eval \$(aws ecr get-login --no-include-email --region eu-central-1 | sed 's|https://||')") 
                // sh "docker build --network=host -t $IMAGE -f deploy/docker/Dockerfile ."
                sh "docker build --network=host -t $IMAGE -f Dockerfile ."
                docker.withRegistry("https://$ECRURL"){
                docker.image("$IMAGE").push("$BUILD_NUMBER")
            }
            }
        }
      }
      // stage('Update Helm appVersion') {
      //   steps {
      //       echo 'Update appVersion'
      //       sh '''
      //             cat helm/Chart.yaml.template | sed "s/appVersion: .*/appVersion: \"${BUILD_NUMBER}\"/g" > helm/Chart.yaml
      //         '''
      //   }
      // }
    }

        post
    {
        always
        {
            sh "docker rmi -f $IMAGE "
        }
    }
} 