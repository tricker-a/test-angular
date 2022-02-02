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
         sh "aws s3 ls"
		     sh "aws s3 mb s3://ibolit-test --region eu-north-1"
         sh "aws s3 website s3://ibolit-test --index-document index.html"
	       sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
     //  }
      }
    
	}
  }
 }
