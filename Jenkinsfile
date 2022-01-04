pipeline {
  agent any
  stages {
    stage('check') {
      parallel {
        stage('check') {
          steps {
            withChecks(name: 'injected name')
          }
        }

        stage('telega') {
          agent any
          steps {
            telegramSend 'test'
          }
        }

      }
    }

    stage('npm install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      steps {
        sh 'npm run test:ci'
      }
    }

    stage('build') {
      steps {
        sh 'npm run build && pwd && ls -la "dist/TestProjectJenkins/"'
      }
    }

    stage('deploy to S3') {
      steps {
        sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
      }
    }

  }
}