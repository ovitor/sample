pipeline {
  agent any

  triggers {
    pollSCM('*/5 * * * *')
  }

  environment {
    VAULT_TOKEN = credentials('vault_token')
    VAULT_ADDR = "https://vault-1.hvvc.local:8200"
    VAULT_SKIP_VERIFY = 1
  }

  stages {
    stage('init') {
      steps {
        sh 'terraform-0.12 init'
      }
    }
    stage('plan') {
      steps {
        sh 'terraform-0.12 plan -out planned-sample'
      }
    }
    stage('apply') {
      steps {
        sh 'terraform-0.12 apply'
      }
    }
  }
}
