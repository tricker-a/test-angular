pipeline {
  agent any
  stages {
    stage('npm install') {
      steps {
        sh 'npm install'
   publishChecks name: 'test', summary: 'ok', text: '123', title: '123test'
      }
    }

    stage('Test') {
      steps {
        sh 'npm run test:ci'
//        publishChecks(name: 'MyCheck', conclusion: Success, summary: 'OK!')
      }
    }

    stage('build') {
      
      steps {
        sh 'npm run build && pwd && ls -la "dist/TestProjectJenkins/"'
 //       publishChecks(name: 'MyCheck', conclusion: Success, summary: 'OK!')
      }
    }

    stage('deploy to S3') {
      steps {
        sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
      }
    }

   
  }
}
