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
	
    stage('copy to web path') {
			steps {
				sh 'cp -R dist/TestProjectJenkins/* "~/var/www/html/" && ls -la "/var/www/html/"'
			}
		}
		
      stage('deploy to S3'){
          steps{
              sh 'aws s3 cp /var/www/html/index.html s3://ibolit-test'
              sh 'aws s3api put-object-acl --bucket <ibolit-test> --key index.html --acl public-read'
		  }
		  
	  }
  }
}
