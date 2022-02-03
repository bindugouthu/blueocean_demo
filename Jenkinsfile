pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        sh '''./jenkins/build.sh
'''
        archiveArtifacts(artifacts: 'build.tar.gz', fingerprint: true)
      }
    }

    stage('Fluffy Test') {
      steps {
        sh './jenkins/test-all.sh'
      }
    }

    stage('Fluffy Deploy') {
      steps {
        echo 'Deploying...'
        sh './jenkins/deploy.sh'
      }
    }

  }
}