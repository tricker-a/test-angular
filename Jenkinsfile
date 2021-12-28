pipeline {
  agent any
  stages {
    stage('npm install') {
      steps {
        sh 'npm install'
   publishChecks name: 'example', title: 'Pipeline Check', summary: 'check through pipeline',
    text: 'you can publish checks in pipeline script',
    detailsURL: 'https://github.com/jenkinsci/checks-api-plugin#pipeline-usage',
    actions: [[label:'an-user-request-action', description:'actions allow users to request pre-defined behaviours', identifier:'an unique identifier']]
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
