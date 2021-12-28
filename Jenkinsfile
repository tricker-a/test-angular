pipeline {
  agent any
  stages {
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
        gitHubPRStatus githubPRMessage('${GITHUB_PR_COND_REF}runstarted')
      }
    }

    stage('deploy to S3') {
      steps {
        sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
      }
    }

   
  }
}
