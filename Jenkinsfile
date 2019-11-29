pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Starting build'
        sh 'docker build -t app .'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing stage'
      }
    }
    stage('Deploy'){
      steps {
        echo 'Deploy'
      }
    }
  }
}