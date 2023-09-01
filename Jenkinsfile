pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo "compilation"
        sh "sh ./make.sh"
        sh "ls -l"
      }
    }
  }
}
