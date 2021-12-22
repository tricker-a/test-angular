pipeline {
  agent any
  
  stages {
     
    stage('Build') {
      steps {
        sh 'npm install'
      }
   }  
//   stage('Lint') {
//      steps {
//       sh 'npm run lint'
//    } 
//   }
//

    stage('Test') {
      steps {
        sh 'npm run test:ci'
		
     }
    }
	  stage('build') {
      steps {
        sh 'npm run build-prod && pwd && ls -la "dist/TestProjectJenkins/" && ls -la "/var/www/TestProjectJenkins/"'
		
     }
    }

      stage('deploy to S3'){
          steps{
              sh 'aws s3 cp public/index.html s3://ibolit-test'
              sh 'aws s3api put-object-acl --bucket <ibolit-test> --key index.html --acl public-read'
		  }
		  
	  }
  }
}
