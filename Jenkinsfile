library 'pipeline-library'
pipeline {
  agent none
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    skipDefaultCheckout true
    timeout(time: 60, unit: 'MINUTES')
  }
  environment {
    repoOwner = "cloudbees-days"
  }
  stages {
    stage('Build & Push Image') {
      when {
        beforeAgent true
        tag '*'
      }
      steps {
        containerBuildPushGeneric("vuejs-app/cloudbees-days/smee-io", "${TAG_NAME}", "core-workshop") {
          checkout scm
          gitShortCommit()
        }
      }
    }
  }
}
