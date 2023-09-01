pipeline { 
  agent any
  stages {
    stage('agentA') {
      agent any
      steps {
        echo "premier agent - mise en pile"
        sh 'sh ./make.sh'
        stash includes:'code', name: 'binaire'
      }
    }
    stage('agentB') {
      agent any
      steps {
        echo "second agent - recuperation de la pile"
        echo "avant le unstash"
        sh 'ls -l'
        unstash 'binaire'
        echo "apres le unstash"
        sh "ls -l"
      }
    }
  }
}
