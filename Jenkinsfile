pipeline {
   agent any 
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
	     withCredentials([[$calss: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEYID', credentialsid: 'aws-s3-cred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
         sh "aws s3 ls"
		     sh "aws s3 mb s3://ibolit-test" 
	       sh 'aws s3 cp dist/TestProjectJenkins/  s3://ibolit-test  --recursive --acl public-read-write'
      }
    }
    
	}
  }
}
