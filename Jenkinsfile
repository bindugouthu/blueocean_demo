pipeline {
  agent any
  stages {
    stage('Fluffy Build') {
      steps {
        sh '''./jenkins/build.sh
ls -l ./jenkins/*'''
        archiveArtifacts(artifacts: 'build.tar.gz', fingerprint: true)
        echo '${my_env_var}'
      }
    }

    stage('Fluffy Test') {
      steps {
        sh './jenkins/test-all.sh'
        junit(testResults: '**/test-reports/**/*', allowEmptyResults: true)
      }
    }

    stage('Fluffy Deploy') {
      steps {
        echo 'Deploying..'
        sh './jenkins/deploy.sh'
      }
    }

  }
  environment {
    my_env_var = '"my_env_value"'
  }
}