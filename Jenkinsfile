pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/price126/dorakdorak-frontend.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          docker.build('prixe/dorakdorak-frontend:latest')
        }
      }
    }

    stage('Push DockerHub') {
      steps {
        withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
          script {
            docker.image('prixe/dorakdorak-frontend:latest').push()
          }
        }
      }
    }
  }
}
