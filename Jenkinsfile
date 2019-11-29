pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Starting build'
        sh 'docker build -t app:test .'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing stage'
        sh '/bin/nc -vz localhost 8080'
      }
    }
    stage('Push Registry'){
      steps {
        echo 'Deploy'
      }
    }
  }
}