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
        sh 'python3 test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t pbeniwal/hello:v$BUILD_NUMBER .'
      }
    }

    stage('Docker Push') {
      steps {
        sh 'docker push pbeniwal/hello:v$BUILD_NUMBER'
      }
    }
  }
}
