pipeline {
  agent any
  stages {
    stage('aaa') {
      steps {
        withCredentials([
            string(credentialsId: 'SIGNING_KEYID', variable: 'SIGNING_KEYID'),
            string(credentialsId: 'SIGNING_PASSWORD', variable: 'SIGNING_PASSWORD')
            ]) {
          sh '''
            echo "SIGNING_USERID=$SIGNING_KEYID"
            echo "SIGNING_PASSWORD=$SIGNING_PASSWORD"
          '''
        }
      }
    }
    stage('initialize') {
      steps {
        sh 'pwd'
        sh 'env'
        sh 'ls -la'
        sh 'java -version'
        sh './gradlew -version'
      }
    }
    stage('build') {
      steps {
        withCredentials([
            string(credentialsId: 'SIGNING_KEYID', variable: 'SIGNING_KEYID'),
            string(credentialsId: 'SIGNING_PASSWORD', variable: 'SIGNING_PASSWORD')
            ]) {
          sh './gradlew build'
        }
      }
    }
  }
}