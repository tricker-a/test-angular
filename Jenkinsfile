pipeline {
//   agent any 
  agent {label 'dev_lab_2'}
	stages {
		stage('Install') {
			steps {
				sh 'npm install'
			}
		}
//		stage('Lint') {
//			steps {
//				sh 'npm run lint'
//			}
//		}
            
		stage('Test') {
			steps {
				sh 'npm run test:ci'
			}
		}
   
    stage('Build') {
			steps {
				sh 'npm run build-prod && pwd && ls -la "dist/TestProjectJenkins/"'
			}
		}
    
    stage('copy to web path') {
			steps {
				sh 'ls -la "/var/www/TestProjectJenkins/" &&  cp -R dist/TestProjectJenkins/* "/var/www/TestProjectJenkins/" && ls -la "/var/www/TestProjectJenkins/"'
			}
		}
    
	}
  
}
