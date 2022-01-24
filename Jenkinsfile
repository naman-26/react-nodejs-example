#!/usr/bin/env groovy

pipeline {
  
  agent any
  
  stages {
    
    stage("build image"){
      steps {
        echo "building the docker image..."
        withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
          sh 'docker build -t namanagrawal/demo-app:rnjs-2.0 .'
          sh "echo $PASS | docker login -u $USER --password-stdin"
          sh 'docker push namanagrawal/demo-app:rnjs-2.0'
        }
      }
  }
  
}
