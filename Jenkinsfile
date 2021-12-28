pipeline {
  agent any
  stages {
  
     stage('checkout') {
        steps {
  checkout([$class: 'GitSCM', branches: [[name: '*/Andrey']], extensions: [], userRemoteConfigs: [[credentialsId: '3', url: 'https://github.com/EugineBelfer/TestAngularJenkins']]])
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
