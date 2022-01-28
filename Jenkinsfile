pipeline {
  agent any
  stages {
    
    stage('npm install') {
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

    stage('deploy') {
      steps {
        	sh '''
          rm -rf  dist
          rm -rf node_modules
          docker build -t testangular:v-"${BUILD_ID}" .
        '''
      }
    }

  }
}
