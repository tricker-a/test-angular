pipeline {
   agent any  
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
	}
  
}
