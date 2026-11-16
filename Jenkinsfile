pipeline {
  agent any

  tools {
    nodejs 'Node16'
  }

  environment {
    CHROME_BIN = '/usr/bin/chromium'
  }

  stages {
    stage('Source') {
      steps {
        git branch: 'master', url: 'https://github.com/ditindia8892/estore-admin.git'
      }
    }
    stage('Compile') {
      steps {
        sh 'npm install --legacy-peer-deps'
      }
    }
    stage('Test') {
      steps {
        sh 'npx ng test --watch=false --browsers=ChromeHeadlessCI'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
  }

  post {
    success {
      archiveArtifacts artifacts: 'dist/**', fingerprint: true
    }
  }
}
