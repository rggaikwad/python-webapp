pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'rm -fr test-reports/'
        sh 'pip install -r requirements.txt'
      }
    }
    stage('test') {
      steps {
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
    stage('docker') {
      steps {
        sh 'docker build -t pbeniwal/hello:$BUILD_NUMBER .' 
      }
    }
  }
}
