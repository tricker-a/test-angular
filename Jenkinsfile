pipeline {
   agent any 
  environment {
    THE_BUTLER_SAYS_SO=credentials('aws-s3-cred')
  }
	stages {
		stage('Install') {
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
    
    stage('copy to web path') {
			steps {
				sh 'cp -R dist/TestProjectJenkins/* "/var/www/TestProjectJenkins/" && ls -la "/var/www/TestProjectJenkins/"'
			}
		}
		stage('deploy to S3') {
      steps {
 //       withAWS(credentials: 'aws-s3-cred', region: 'eu-north-1') {
    //     sh "aws s3 ls"
		 //    sh "aws s3 mb s3://ibolit-test --region eu-north-1"
         sh "aws s3 website s3://ibolit-test --index-document index.html"
	       sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test/new  --recursive --acl public-read-write'
         sh 'aws s3 --recursive mv s3://ibolit-test/actual s3://ibolit-test/old --acl public-read-write'
         sh 'aws s3 --recursive mv s3://ibolit-test/new s3://ibolit-test/actual --acl public-read-write'
          sh 'aws s3 --recursive mv  s3://ibolit-test/actual  s3://ibolit-test  --acl public-read-write'
      //  sh 'aws s3 sync dist/TestProjectJenkins/  s3://ibolit-test --delete --acl public-read'
     //  }
      }
    
	}
  }
 }
