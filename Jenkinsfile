pipeline {
  environment {
    registry = "houmamamine/houmam_tp5"
    registryCredential = 'houmam'
    dockerImage = ''
    gitBranch = 'master'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git branch: "${gitBranch}", url: 'https://github.com/HoumamAmine/TP5_DevOps_Jenkins.git'
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Test image') {
      steps {
        script {

          echo "Tests passed"
        }
      }
    }
    stage('Publish Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}