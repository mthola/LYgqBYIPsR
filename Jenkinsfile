pipeline {
  agent {
    kubernetes {
      label 'jenkins-k8s-slave'  // all your pods will be named with this prefix, followed by a unique id
      idleMinutes 5  // how long the pod will live after no jobs have run on it
      yamlFile 'build-pod.yaml'  // path to the pod definition relative to the root of our project 
      defaultContainer 'maven'  // define a default container if more than a few stages use it, will default to jnlp container
    }   
  }
  environment {
    SERVICE_NAME = 'tech-challenge'
    SERVICE_GROUP = 'credence'
    SERVICE_BUILD = 'dev'
  }
  stages {
    stage('Build') {
      steps {  // no container directive is needed as the maven container is the default
        script {
            sh ("echo 'build steps'")
        }
      }
    }
    stage('Build Docker Container') {
      steps {
        script {
          container('docker') {   // demonstrates building, but not deploying
            script{
                sh ('echo "I am inside of docker container"')
            }
            }
          }
        }
      }
    stage('Test') {
      steps {
        script {
          container('docker') {
            script{
                sh ('echo deploying phase')
            }
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        script {
          container('docker') {
            script{
                sh ('echo deploying phase')
            }
          }
        }
      }

    }
  }
}
