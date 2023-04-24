pipeline {
  agent {
    node {
      label 'swe-645-a2'
    }
  }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'rm -rf *.war'
        sh 'jar -cvf SWE645-Assignment2.war -C WebContent/ .'
      }
      post {
        success {
          archiveArtifacts artifacts: '*.war', fingerprint: true
        }
      }
    }
    stage('Docker Build and Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
          sh "echo ${PASSWORD} | sudo docker login -u ${USERNAME} --password-stdin"
          sh "sudo docker build -t 'sanjanagovindu/swe645-a2' ."
          sh "sudo docker push sanjanagovindu/swe645-a2"
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        sh "kubectl rollout restart deploy deployment-a2 -n namespace-h2"
      }
    }
  }
}
