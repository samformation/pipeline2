pipeline {
  agent any
  environment {
    TAGPRJ = 'cmode'
  }
  stages {
    stage('build') {
      steps {
        echo "compilation"
        sh "sh ./make.sh"
        sh "ls -l"
        archiveArtifacts artifacts:'code', fingerprint: true
      }
    }
    stage('deploy') {
      when {
        expression {
          currentBuild.result == 'SUCCESS' || currentBuild.result == null
        }
      }
      steps {
        sh "mv code code-${TAGPRJ}-${BUILD_NUMBER}"
        sh "ls -l"
        echo "deploy"
      }
    }
  }
}

