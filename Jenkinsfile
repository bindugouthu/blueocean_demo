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
      parallel {
        stage('backend') {
          steps {
            sh './jenkins/test-backend.sh'
            junit(testResults: './reports/backend-test-reports/**/*', allowEmptyResults: true)
          }
        }

        stage('frontend') {
          steps {
            sh './jenkins/test-frontend.sh'
            junit(testResults: './reports/frontend-test-reports/', allowEmptyResults: true)
          }
        }

        stage('performance') {
          steps {
            sh './jenkins/test-performance.sh'
            junit(testResults: './reports/performance-test-reports/', allowEmptyResults: true)
          }
        }

        stage('static') {
          steps {
            sh './jenkins/test-static.sh'
            junit(testResults: './reports/static-test-reports/', allowEmptyResults: true)
          }
        }

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