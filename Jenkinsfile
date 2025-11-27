pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        // default checkout from pipeline SCM
        checkout scm
      }
    }

    stage('Run script') {
      steps {
        script {
          if (isUnix()) {
            // Unix/Linux node -> run with sh
            sh 'chmod +x ./routepulse.sh || true'
            sh './routepulse.sh'
          } else {
            // Windows node -> run an equivalent using bat
            // Option 1: if you have Git Bash on PATH, you can use bash:
            // bat 'bash ./routepulse.sh'

            // Option 2 (safe, always available): just run the command directly on Windows
            // (this replicates the behavior of the script)
            bat 'echo RoutePulse service online for CIE set 103'
          }
        }
      }
    }
  }

  post {
    success { echo 'Build finished: SUCCESS' }
    failure { echo 'Build finished: FAILURE' }
  }
}
