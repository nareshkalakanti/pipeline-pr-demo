pipeline {

  agent any

  options {
    timestamps()
  }

  stages {
    stage('PHPUnit Test') {
      steps {
        echo 'Running PHPUnit...'
        sh '''
        echo "hello World"
        '''
      }
    }
    stage('Merge PR') {
      when {
        branch 'PR-*'
      }
      steps {
        sh 'git remote set-url origin git@github.com:nareshkalakanti/pipeline-pr-demo.git'
        sh 'git remote set-branches --add origin ${CHANGE_TARGET}'
        sh 'git fetch origin'
        sh 'git checkout ${CHANGE_TARGET}'
        sh 'git merge --no-ff ${GIT_COMMIT}'
        sh 'git push origin ${CHANGE_TARGET}'
      }
    }
  }
}