pipeline {
  agent any
  environment {
    TAGPRJ = 'cmode'
    SECRET = credentials('valeur_du_secret')
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
        sh "mv code code-${TAGPRJ}-${SECRET}-${BUILD_NUMBER}"
        sh "ls -l"
        echo "deploy"
      }
    }
  }
}

