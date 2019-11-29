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
        sh 'docker run -d --rm -p 80:80 --name app app:test'
        sh '/bin/nc -vz localhost 80'
        sh 'docker stop app'
      }
    }
    stage('Push Registry'){
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerCredentials', passwordVariable: 'password', usernameVariable: 'user')]) {
        echo "USER: $user"
        sh 'docker login -u $user -p $password'
        sh 'docker tag app:test jafaramirez/app:stable'
        sh 'docker push jafaramirez/app:stable'
        }
      }
    }
  }
}