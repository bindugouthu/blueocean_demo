pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        echo 'Placeholder'
        sh 'echo "./jenkins/build.sh"'
      }
    }

    stage('Fluffy Test') {
      steps {
        sh 'sleep 5'
        sh 'echo "./jenkins/test-all.sh"'
      }
    }

    stage('Fluffy Deploy') {
      steps {
        echo 'Deploying...'
      }
    }

  }
}