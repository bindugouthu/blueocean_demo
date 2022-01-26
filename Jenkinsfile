pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        echo 'Placeholder'
        sh '''./jenkins/build.sh
ls -l ./jenkins/build.sh '''
        archiveArtifacts(artifacts: 'build.tar.gz', fingerprint: true)
      }
    }

    stage('Fluffy Test') {
      steps {
        sh 'sleep 5'
        sh './jenkins/test-all.sh'
      }
    }

    stage('Fluffy Deploy') {
      steps {
        echo 'Deploying...'
      }
    }

  }
}