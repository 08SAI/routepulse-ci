pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Run script') {
      steps {
        sh 'chmod +x ./routepulse.sh'
        sh './routepulse.sh'
      }
    }
  }

  post {
    success {
      echo 'Build finished: SUCCESS'
    }
    failure {
      echo 'Build finished: FAILURE'
    }
  }
}
