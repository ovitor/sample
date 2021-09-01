pipeline {
  agent any

  triggers {
    pollSCM('*/5 * * * *')
  }

  environment {
    VAULT_TOKEN = credentials('vault_token')
  }

  stages {
    stage('pre-build') {
      steps {
        echo 'this is the pre build stage'
        sh 'terraform-0.12 version'
        sh 'vault version'
        sh 'terraform init'
      }
    }
    stage('plan') {
      steps {
        sh 'terraform plan -out planned-sample'
      }
    }
    stage('apply') {
      steps {
        sh 'terraform apply'
      }
    }
  }
}
