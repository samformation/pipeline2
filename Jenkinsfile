pipeline {
  agent any
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
        echo "deploy"
      }
    }
  }
}

