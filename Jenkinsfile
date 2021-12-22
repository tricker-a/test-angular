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
        sh 'npm run build && pwd && ls -la "dist/TestProjectJenkins/"'
		
     }
    }
//	
//   stage('copy to web path') {
//			steps {
//				sh 'cp -R dist/TestProjectJenkins/* "/.www/"'
//			}
//		}
		
      stage('deploy to S3'){
          steps{
              sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
		  }
		  
	  }
  }
}
