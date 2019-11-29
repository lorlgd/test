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
        sh 'docker run -d -p 80:80 --rm app'
        sh '/bin/nc -vz localhost 80'
        sh 'docker stop app'
      }
    }
    stage('Push Registry'){
      steps {
        sh 'docker tag app:test jafaramirez/app:stable'
        sh 'docker push jafaramirez/app:stable'
      }
    }
  }
}